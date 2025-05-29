```
pitch2xml(pitch)
```

与えられたピッチ（MIDI）の musicxmls 値を返します。

pitch::UInt8 : C-1 から始まり、半音ごとに 1 を加えます。

![楽譜上の音程のステップとオクターブ](docs/pitchesonstaff.png) ![ギター上の音程](docs/pitchesonguitar.png) ![フルキーボード上の音程](docs/fullpiano.gif)

MIDI.jl から修正されました

# 例:

```julia
pitch = 0 # C-1 の場合
step, alter, octave = pitch2xml()
```
