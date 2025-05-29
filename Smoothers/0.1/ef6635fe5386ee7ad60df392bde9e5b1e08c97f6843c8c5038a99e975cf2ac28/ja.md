パッケージ: Forecast

```
loess(xv, yv;
      d = 0,
      q = 3*sum((!ismissing).(yv))÷4,
      rho = fill(1.0,length(yv)),
      exact = [], extra = [])

loess(yv;
      d = 0,
      q = 3*sum((!ismissing).(yv))÷4,
      rho = fill(1.0,length(yv)),
      exact = [], extra = [])
```

観測値のベクトルを局所加重回帰を使用して平滑化する関数を返します。

loessは任意の数の独立変数に対して観測値を平滑化するために使用できますが、この実装は単変量です。loessの速度は線形フィッティング計算のための高速近似を使用することで大幅に向上できますが、この実装では正確な結果も計算できます。

loessの機能と名称は以下の文献に基づいています：

"STL: A Seasonal, Trend Decomposition Procedure Based on Loess" Robert B. Cleveland, William S. Cleveland, Jean E. McRae, and Irma Terpenning. Journal of Official Statistics Vol. 6. No. 1, 1990, pp. 3-73 (c) Statistics Sweden.

# 引数

  * `xv`: 観測値のサポート。提供されない場合は1:length(yv)が代わりに使用されます。
  * `yv`: 観測値。
  * `d`: 線形フィットの次数。0、1、または2の値を受け入れます。0の場合、`d`の推定値が計算されます。
  * `q`: qが増加するにつれてloessはより滑らかになります。qが無限大に近づくと、loessは次数`d`の通常の最小二乗多項式フィットに近づきます。デフォルトはxvの非欠損値の長さの3/4の丸めです。
  * `rho`: 観測値の信頼性を表す重み（例：yiが分散σ^2*kiを持ち、kiが知られている場合、rhoiは1/kiになる可能性があります）。デフォルトは1です。
  * `exact`: 正確なloessが計算されるサポート値を含むベクトル。値が少ないほどloessは速くなります。デフォルトは空の配列です。10値以下の系列の場合、正確なloessが保証されます。
  * `extra`: ヒューリスティックによって選択された値の他に、正確なloessが計算されるサポート値を含むベクトル。

# 戻り値

`exact`に含まれる値の正確なloessを返し、残りの値には正確なloessまたは高速近似を返す関数。

# 例

```julia-repl
n = 1000
x = sort(rand(n)*2*pi);
y = sin.(x) + randn(n);
f = Smoothers.loess(x,y)
isapprox(f(pi),0;atol=0.1) #true
[...]
```
