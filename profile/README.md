# Renotion

Renotion allows you to wrap your Notion Page with a long url as a custom domain.

For instance, Notion Page like `https://your-project.notion.site/Page-Name-thirtytwocharacterslongpageident`
becomes `your-project.com`.

All you need is a domain and a crypto wallet.

## How it works
1. First, you register your page-to-domain association at [renotion.xyz](https://renotion.xyz/)
    - You own your registration: it's stored on the blockchain (Polygon)
    - There's a symbolic one-time payment associated as I have to run some infra in order to facilitate the Notion page wrapping
2. Then you configure DNS for your domain
    - You will be asked to configure both CNAME and TXT (for domain verification and TLS certificate issuance)
3. When DNS is configured – you're good to go!

## Architecture
![](https://raw.githubusercontent.com/renotion-xyz/.github/main/profile/assets/schema.jpg)

### Worker
- Page-to-domain association is stored on the blockchain
- When your domain is visited, in fact the request is handled by `abc.renotion.xyz`, which is a Cloudflare worker
- Worker looks up your domain in the blockchain, finds the associated page and serves it

### API Backend
- When you interact with the blockchain via web3-app at [renotion.xyz](https://renotion.xyz) it makes requests to `api.renotion.xyz`
- API allows to fetch page registration metadata from the blockchain
- When metadata is fetched (domain hostname), it then asserts CNAME configuration and TLS certificate issuance for the domain

### Smart Contract
- Renotion uses Polygon as a blockchain technology
- Smart Contract address: [0xD189E333277a8dbd65244A97bE3ecBE4f7Bee5cf](https://polygonscan.com/address/0xD189E333277a8dbd65244A97bE3ecBE4f7Bee5cf)

### Web3 app
- The app allows you to check your pages status and register a new page
- It tracks CNAME/TXT records statuses and provides relevant information
- You can also use variety of crypto wallets to use the app

---
## Contact

- [hello@renotion.xyz](mailto:hello@renotion.xyz)
- [t.me/quiker](https://t.me/quiker)
