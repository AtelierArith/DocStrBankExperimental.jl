```
reli1(x::Real)
```

実数 `Real` 型の実数 $x$ に対する1次ポリログarithmの実部 $\Re[\operatorname{Li}_1(x)] = -\Re[\ln(1 - z)]$ を返します。

著者: アレクサンダー・フォイヒト

ライセンス: MIT

# 例

```jldoctest; setup = :(using PolyLog)
julia> reli1(0.5)
0.6931471805599453

julia> reli1(BigFloat("0.5"))
0.6931471805599453094172321214581765680755001343602552541206800094933936219696955
```
