```
init!(d; block_size=256, samplerate=44100)
```

DSPBlock `d` を使用するために初期化します。

`compute!` の前に呼び出す必要があります。古い DSP インスタンスは削除されるため、これを繰り返し呼び出すことができ、内部状態などがリセットされます。
