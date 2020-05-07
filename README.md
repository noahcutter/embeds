# VPR's Homepage Block Embeds

Core Publisher homepages currently lack the ability to easily embed mp3s and iframes into blocks. This repository shows what Vermont Public Radio is using to work around the problem. These files live on our S3 account and are called in Core Publisher's `Promotional Blocks` through html in subheading fields. Big thanks to KUNC's Jim Hill and KBIA's Nathan Lawrence for their help. Original documentation here by Sara Simon, updated by Noah Cutter.


## Set Up

The first step is to create an html file that contains the iframe. This repository contains the code for iframes that are currently embedded onto [www.vpr.org](https://www.vpr.org). For basic iframe embeds, follow `template.html`. For a SoundCloud embed, see `wintry-mix.html`. For jplayer, follow `newscast.html`. The CSS at the top of `newscast.html` was styled by Jim Hill to match Core Publisher's audio play buttons. Major points to Jim for that.

For pym.js, follow the instructions [here](http://blog.apps.npr.org/pym.js/). With Core Publisher, be sure to use the pym.js loader version.


## Deploy

Push the html file up to Amazon S3. At VPR, we created a folder within S3 called `embed` and push everything there. For example, if we were to push the `template.html` file from this repository up to VPR's S3 account, I should be able to head to `app.vpr.org/embed/template.html` and see my iframe live. Don't forget to click the "make public" button. That's very important.


## Embed into Core Publisher

Within the block factory, create a new promotional block. In the subheading field, call your new live version of the iframe, along with the reference to pym.js.

`<div data-pym-src="https://app.vpr.org/embed/subscribe-but-why.html"></div> <script type="text/javascript" src="https://pym.nprapps.org/pym-loader.v1.min.js"></script>`

Important to note: If adding a pym.js embed to a post, you'll need a different template. Core Publisher doesn't love those `div` fields. Instead, follow this:

`<p data-pym-src="https://app.vpr.org/embed/subscribe-but-why.html">Loading...</p><script type="text/javascript" src="https://pym.nprapps.org/pym-loader.v1.min.js"></script>`
