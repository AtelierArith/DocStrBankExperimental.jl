パッケージ: Smoothers

```
filter(b,a,x,si)
```

次の線形時間不変差分方程式を使用して、xにデジタルフィルターを適用します。

$$
y(n) = \sum_{k=0}^M d_{k+1} \cdot x_{n-k}-\sum_{k=1}^N c_{k+1} \cdot y_{n-k} 
\\ \forall n | 1\le n \le \left\| x \right\| | c=a/a_1, d=b/a_1
$$

実装は、[Octave filter function](https://octave.sourceforge.io/octave/function/filter.html) の説明に従います。

# 引数

  * `a`: フィルターの有理伝達関数の分子係数のベクトル。
  * `b`: フィルターの有理伝達関数の分母係数のベクトル。
  * `x`: データのベクトル。
  * `si`: 初期状態のベクトル。

# 戻り値

フィルタリングされたデータのベクトル

# 例

```julia-repl
using Plots

t = Array(LinRange(-pi,pi,100));
x = sin.(t) .+ 0.25*rand(length(t));

# 移動平均フィルター
w = 5; 
b = ones(w)/w;
a = [1];

plot(t,x,label="sin(x)",legend=:bottomright)
y1 = filter(b,a,x)
si = x[1:4] .+ .1;
y2 = filter(b,a,x,si)
plot!(t,y1,label="MA")
plot!(t,y2,label="MA with si")
```
