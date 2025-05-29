```
WolfePowellBinaryLinesearch <: Linesearch
```

A [`Linesearch`](@ref) メソッドは、バイナリーチョップに基づいてウルフ条件を満たすステップサイズ `t` を決定します。

ここで、$η$ は探索方向、$c1,c_2>0$ は2つの定数とします。次に、

$$
A(t) = f(x_+) ≤ c1 t ⟨\operatorname{grad}f(x), η⟩_{x}
\quad\text{and}\quad
W(t) = ⟨\operatorname{grad}f(x_+), \text{V}_{x_+\gets x}η⟩_{x_+} ≥ c_2 ⟨η, \operatorname{grad}f(x)⟩_x,
$$

ここで、$x_+ = \operatorname{retr}_x(tη)$ は現在の試行点であり、$\text{V}$ はベクトル輸送です。次に、以下のアルゴリズムが [Huang:2014](@cite) のアルゴリズム7に似て実行されます。

1. $$
    α=0
    $$

    , $β=∞$ および $t=1$ を設定します。
2. $$
    A(t)
    $$

    が成り立たないか、$W(t)$ が成り立たない限り、ステップ3-5を実行します。
3. $$
    A(t)
    $$

    が失敗した場合、$β=t$ を設定します。
4. $$
    A(t)
    $$

    が成り立つが $W(t)$ が失敗した場合、$α=t$ を設定します。
5. $$
    β<∞
    $$

    の場合は $t=\frac{α+β}{2}$ を設定し、そうでない場合は $t=2α$ を設定します。

# コンストラクタ

2つのコンストラクタが存在し、最初の（オプションの）パラメータとして多様体 `M` が提供されると、そのデフォルトの再収束とベクトル輸送がデフォルトになります。この場合、再収束とベクトル輸送も使いやすさのためにキーワード引数として指定できます。もう1つのコンストラクタは後方互換性のために保持されています。

```
WolfePowellLinesearch(
    M=DefaultManifold(),
    c1::Float64=10^(-4),
    c2::Float64=0.999;
    retraction_method = default_retraction_method(M),
    vector_transport_method = default_vector_transport(M),
    linesearch_stopsize = 0.0
)
```
