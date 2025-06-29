```
iterator([rng, ], r::NominalRange, [,n])
iterator([rng, ], r::NumericRange, n)
```

`ParamRange`オブジェクト`r`のためのイテレータ（現在はベクトル）を返します。最初のケースでは、範囲に格納されているすべての`values`を反復処理します（または`n`が指定されている場合は最初の`n`のみ）。2番目のケースでは、次のように生成された約`n`の順序付けられた値を反復処理します：

1. 最初に、`U`と`L`の間に正確に`n`の値が生成され、間隔は`r.scale`によって決定されます（`scale=:linear`の場合は均一）`U`と`L`は次の表によって与えられます：

    | `r.lower` | `r.upper` |                 `L` |                 `U` |  | ––––-:| ––––-:| –––––––––-:| –––––––––-:|  |    有限   |    有限   |           `r.lower` |           `r.upper` |  |    `-Inf` |    有限   | `r.upper - 2r.unit` |           `r.upper` |  |    有限   |     `Inf` |           `r.lower` | `r.lower + 2r.unit` |  |    `-Inf` |     `Inf` | `r.origin - r.unit` | `r.origin + r.unit` |
2. 呼び出し可能な`f`が`scale`として提供される場合、(1)では常に均一な間隔が適用されますが、`f`は結果に対してブロードキャストされます。（通常のスケールとは異なり、これは生成される値の実効範囲を変更し、単に間隔を変更するのではありません。）
3. `r`が離散的な数値範囲（`r isa NumericRange{<:Integer}`）である場合、値はさらに丸められ、重複する値は削除されます。そうでなければ、すべての値が使用されます（そして正確に`n`の値があります）。
4. 最後に、ランダム数生成器`rng`が指定されている場合、値はランダムな順序で返されます（重複なしのサンプリング）、そうでなければ数値順に返されるか、`NominalRange`の場合は範囲コンストラクタに提供された順序で返されます。
