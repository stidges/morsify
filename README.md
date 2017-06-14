# morsify

[![npm-version]][npm] [![npm-downloads]][npm] [![travis-ci]][travis]

Morse code encoder and decoder with no dependencies supports Latin, Cyrilic, Greek, Hebrew, 
Arabic, Persian, Japanese, and Korean characters with audio generation functionality.

## Installation

### npm

```bash
$ npm install morsify --save
```

### yarn

```bash
$ yarn add morsify
```

## Usage

```js
var morsify = require('morsify');

morsify.encode('SOS'); // .../---/... 
morsify.decode('.../---/...'); // S O S
morsify.audio('SOS'); // will return base64 encoded audio/wav data
```

Or alternatively, you can also use the library directly with including the source file.

```html
<script src="https://rawgit.com/ozdemirburak/morsify/master/index.js"></script>
<script>
    console.log(morsify.encode('SOS')); // .../---/... 
    console.log(morsify.decode('.../---/...')); // S O S
    console.log(morsify.audio('SOS')); // will return base64 encoded audio/wav data
</script>
```

## Options and Localization

You can customize the dash, dot or space characters and specify the alphabet with the priority option for
an accurate encoding and decoding.
 
What priority option does is, gives direction to the plugin to start to searching for the given character set first.

Set the priority option according to the list below.

- 1 => ASCII (Default)
- 2 => Numbers
- 3 => Punctuation
- 4 => Latin Extended (Turkish, Polski etc.)
- 5 => Cyrilic
- 6 => Greek
- 7 => Hebrew
- 8 => Arabic
- 9 => Persian
- 10 => Japanese
- 11 => Korean

```js
morsify.encode('Ленинград', { priority: 5 }) // .-.././-./../-./--./.-./.-/-..
morsify.decode('.../.-/--./.-/.--./.--', { priority: 6 }) // Σ Α Γ Α Π Ω
morsify.decode('––– –... ––– –. ––. .. .–.. –––', { dash: '–', dot: '.', space: ' ', priority: 7 }) // ה ב ה נ ג י ל ה
morsify.audio('البُراق‎‎', { // generates the morse .-/.-../-.../.-./.-/--.- then generates the audio from it
  channels: 1, 
  sampleRate: 1012, 
  bitDepth: 16,
  unit: 0.1,
  frequency: 440.0,
  volume: 32767,
  priority: 8
})
```

## Contributing

Contributions are welcome. 

Currently, as a major drawback, Chinese characters are missing. Someone with the knowledge of 
[Chinese telegraph code](https://en.wikipedia.org/wiki/Chinese_telegraph_code) can help to implement it. Also someone who is proficient in Thai can help
to include [Thai alphabet](https://th.wikipedia.org/wiki/รหัสมอร์ส).

## License
The MIT License (MIT). Please see [License File](LICENSE) for more information.

  [npm-version]: https://img.shields.io/npm/v/morsify.svg?style=flat-square
  [npm-downloads]: https://img.shields.io/npm/dm/morsify.svg?style=flat-square
  [travis-ci]: https://img.shields.io/travis/ozdemirburak/morsify/master.svg?style=flat-square

  [npm]: https://www.npmjs.com/package/morsify
  [travis]: https://travis-ci.org/ozdemirburak/morsify
