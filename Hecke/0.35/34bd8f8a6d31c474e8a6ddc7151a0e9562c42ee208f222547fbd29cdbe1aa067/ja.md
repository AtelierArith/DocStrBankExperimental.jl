```
integral_closure(R, F)
```

リング $R$ の $F$ における整数閉包を計算します。$F$ は $R$ の分数体に対する有限拡大である必要があります。このアルゴリズムは、Round-2 メソッドの変種を使用します。

現在サポートされているのは

  * $$
    R
    $$

    整数であり、$F$ は（絶対単純な）数体です。ここでの結果は数体の位数です。
  * $$
    R
    $$

    整数の局所化であり、$F$ は（絶対単純な）数です。ここでの結果は一般的な位数です。
  * $$
    R
    $$

    体 $k$ 上の一変数多項式環であり、$F$ は関数体（$k(t)$ の有限拡大）です。
  * $$
    R
    $$

    体 $k$ 上の一変数多項式環の次数局所化であり、$F$ は $k(t)$ の有限拡大です。
  * $$
    R
    $$

    整数上の一変数多項式環であり、$F$ は有理体 $Q$ の $Q(t)$ の有限拡大です。

# 例

```julia
julia> k, a = quadratic_field(12);

julia> integral_closure(ZZ, k)

Maximal order of real quadratic field defined by x^2 - 12
with basis AbsSimpleNumFieldElem[1, 1//2*sqrt(12)]
```
