```
gmtvector(cmd0::String="", arg1=nothing, kwargs...)
```

1次元データテーブルの時間領域フィルタリング。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`gmtvector`](http://docs.generic-mapping-tools.org/latest/gmtvector.html)を参照してください。

## パラメータ

  * **A** | **primary_vec** :: [Type => Str]   `Arg = m[conf]|vector`

    テーブルを読み込む代わりに、単一の主要ベクトルを指定します。
  * **C** | **cartesian** :: [Type => Str | []]        `Arg = [i|o]`

    入力と出力の直交座標を選択します。
  * **E** | **geod2geoc** :: [Type => Bool]

    入力の地理座標を測地から地心に変換し、出力の地理座標を地心から測地に変換します。
  * **N** | **normalize** :: [Type => Bool]

    出力を報告する前に結果ベクトルを正規化します。
  * **S** | **secondary_vec** :: [Type => Str | List]    `Arg = [vector]`

    最初のベクトルと同じ形式の単一の二次ベクトルを指定します。
  * **T** | **transform** :: [Type => Str | List]     `Arg = a|d|D|paz|s|r[arg|R|x]`

    興味のあるベクトル変換を指定します。
