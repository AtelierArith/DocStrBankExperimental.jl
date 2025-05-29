```
@MX
```

`MX.`をMusicXMLタイプの名前に追加するマクロです。

MusicXMLのタイプは、他のライブラリ（例えば`Dates.Time`や`MIDI.Note`）の同様の名前のタイプとの競合を避けるためにパッケージからエクスポートされていないため、MusicXMLタイプを使用するための便利な`@MX`が提供されています。

`@MX`は、マクロの前にある`()`内や`begin end`の間にあるこれらの名前のタイプが明示的に書かれていない限り、MusicXMLタイプであると仮定します（例：`MIDI.Note`）。

!!! warn
    文字列内で使用されている場合、タイプの名前が置き換えられます。


# 例

```julia
@MX begin
    Note(pitch = Pitch(step = "C", alter = 0, octave = 4), duration =  4))
    # すべてのコード ...
end
```

は次のように変換されます：

```julia
    MX.Note(pitch = Pitch(step = "C", alter = 0, octave = 4), duration =  4))
```

別のライブラリから明示的に呼び出された場合、タイプは変更されません：

```julia
@MX Dates.Time(12,53,40)
```

は次のように残ります：

```julia
Dates.Time(12,53,40)
```
