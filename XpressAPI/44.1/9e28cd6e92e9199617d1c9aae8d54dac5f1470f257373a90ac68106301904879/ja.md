```
XPRSaddpwlcons(prob, npwls, npoints, colind, resultant, start, xval, yval)::prob
```

1つ以上の区分線形制約を問題に追加します。

各区分線形制約 `y = f(x)` は、（入力）列 x、（異なる）結果（出力列）y、および区分線形関数 f で構成されます。区分線形関数 f は、x 値と y 値の組み合わせとして与えられる少なくとも 2 つのブレークポイントによって説明されます。非連続の区分線形関数もサポートされており、この場合、特定の点での左限界と右限界の両方をブレークポイントとして入力する必要があります。左限界と右限界を区別するために、ブレークポイントは非減少の x 値のリストとして与える必要があります。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `npwls::Integer`: 追加する区分線形制約の数。
  * `npoints::Integer`: 追加すべきすべての区分線形制約のブレークポイントの合計数。
  * `colind::AbstractVector{Integer}`: 区分線形関数の入力変数 x のインデックスを含む長さ `npwls` の整数配列。
  * `resultant::AbstractVector{Integer}`: 区分線形関数の出力変数 y のインデックスを含む長さ `npwls` の整数配列。
  * `start::AbstractVector{Integer}`: `xval` および `yval` 配列における各区分線形制約の開始インデックスを含む長さ `npwls` の整数配列。
  * `xval::AbstractVector{Number}`: ブレークポイントの x 値を含む長さ `npoints` の倍精度配列。
  * `yval::AbstractVector{Number}`: ブレークポイントの y 値を含む長さ `npoints` の倍精度配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C API の対応する関数 [XPRSaddpwlcons](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddpwlcons.html) のドキュメントも参照してください。
