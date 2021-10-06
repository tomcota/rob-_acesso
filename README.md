# rob-_acesso
Criação de um robô que faz login com a biblioteca pupperteer
const puppeteer = require('puppeteer');

(async () => {
  const browser = await puppeteer.launch({headless:false});
  const page = await browser.newPage();
  
  //setViewport para melhorar a dimensão da pagina
  await page.setViewport({
    width:1200,
    height:600
  })
  await page.goto('https://sitedesejado');
  await page.waitFor('input[name="username"]');
  await page.type('input[name="username"]','Login',{delay:100});
  await page.type('input[name="password"]','senha',{delay:100});
  await page.keyboard.press('Enter');
  
  //clicar selecionar campo e digitar referencia do combox
  await page.waitFor('input[nome do botão1]'); // ex nome do botão id="input-855
  await page.type('input[nome do botão1]'),'referencia',{delay:100});

  await page.waitFor('input[nome do botão2]'); // ex nome do botão id="input-855
  await page.type('input[nome do botão2]','referencia',{delay:130});
  
  //não encontrei o nome do botão 'conluir' foi necessário usar uma matriz de elementos. 
  // const elements = await page.$x('<xPath>')
  // await elements[0].click() 
  
  const elements = await page.$x('//*[@id="app"]/div/main/div/div/div/div/div/div[5]/div/div/button',{delay:100})
  await elements[0].click() 
  const elements2 = await page.$x('//*[@id="app"]/div/main/div/div[2]/div/div[2]/div/footer/div/div/button[2]')
  await elements2[0].click() 

await browser.close();
})(); 
