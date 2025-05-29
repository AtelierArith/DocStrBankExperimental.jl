```
fitcircle(cmd0::String="", arg1=nothing, kwargs...)
```

球面上の点に対して平均位置と大[または小]円をフィットさせます。

## パラメータ

  * **L** | **norm** :: [Type => Int | []]

    希望するノルムを1または2として指定するか、[]または3を使用して両方の解を表示します。
  * **F** | **coord** | **coordinates** :: [Type => Str]	`Arg = f|m|n|s|c`

    データ座標のみを返し、Argを追加してどの座標を希望するかを指定します。
  * **S** | **small_circle** :: [Type => Number]    `Arg = symmetry_factor`

    試みます

完全なドキュメントを見るには、次のように入力してください: $@? fitcircle$
