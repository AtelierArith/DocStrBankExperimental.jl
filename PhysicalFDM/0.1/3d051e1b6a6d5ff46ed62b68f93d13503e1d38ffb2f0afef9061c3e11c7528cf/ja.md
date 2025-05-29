```julia
diff_mat(n; ...) -> Any
diff_mat(
    n,
    order;
    T,
    dt,
    points,
    lpoints,
    rpoints,
    fitting_order,
    boundary,
    boundary_points,
    boundary_order,
    sparse
) -> Any

```

微分行列を生成します。

# 引数

  * `n`: 行列のサイズ。もし `v` が長さ `n` のベクトルであれば、diff_mat(n)*v は `v` の微分を計算します。
  * `order`: 微分の次数。
  * `T`: 行列要素の型。もし `T=Rational` または `using SymPy` を使用して `T=Sym` を設定すると、`diff_mat` は正確な値を返します。
  * `dt`: 数値微分のステップサイズ。
  * `points`: 微分を推定するための多項式をフィッティングする点の数。この引数は便利のためだけです。実際の点の数は常に `lpoints+rpoints+1` です。
  * `lpoints`: 対象点の左側にある点の数で、フィッティングされた多項式によって微分が計算されます。
  * `rpoints`: 対象点の右側にある点の数。もし `lpoints==rpoints` であれば、微分は中心差分として推定されます。もし `lpoints==0` であれば、通常の前方差分になります。もし `rpoints==0` であれば、後方差分になります。
  * `fitting_order`: 微分を推定するためのフィッティングされた多項式の次数。
  * `boundary`: 境界条件。`Dirichlet()`（境界値はゼロ）、`Periodic()`（データが周期的であると仮定）、`:Extrapolation`（境界値は `boundary_points` と `boundary_order` に従って外挿される）、`:None`（境界を扱わず、非正方行列を返す）から選択できます。
  * `boundary_points`: 境界で微分を推定するための多項式をフィッティングする点の数。通常、`points` よりもかなり少なくないべきであり、そうでないと現在の点が微分を推定するために使用されないことがあります。
  * `boundary_order`: `boundary_points` によって決定された点のためのフィッティングされた多項式の次数。
  * `sparse`: true の場合、密行列の代わりに疎行列を返します。

著者: Qian, Long. 2021-09 (github: longqian95)

# 例

```
k=5; x=rand(k);
diff_mat(k,1;points=3)*x #3点の1次中心微分を行う ((x[n+1]-x[n-1])/2)。
diff_mat(k,2;points=3)*x #3点の2次中心微分を行う (x[n+1]+x[n-1]-2x[n])。
diff_mat(k,1;points=2,lpoints=0)*x #通常の1次前方微分を行う (x[n+1]-x[n])。
diff_mat(k,1;lpoints=1,rpoints=0)*x #1次後方微分を行う (x[n-1]-x[n])。
```
