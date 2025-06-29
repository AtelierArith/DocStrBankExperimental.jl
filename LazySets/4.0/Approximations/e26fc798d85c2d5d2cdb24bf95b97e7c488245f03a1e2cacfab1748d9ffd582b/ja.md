```
overapproximate(X::ConvexHull{N, <:AbstractZonotope, <:AbstractZonotope},
                ::Type{<:Zonotope}) where {N}
```

2つのゾノトピック集合の凸包を過大評価します。

### 入力

  * `X`         – 2つのゾノトピック集合の凸包
  * `Zonotope`  – 目標集合の型
  * `algorithm` – （オプション; デフォルト: `"mean"`）アルゴリズムの選択; 可能な値は `"mean"` と `"join"` です。

### 出力

$$
X ⊆ Z
$$

となるゾノトープ $Z$。

### アルゴリズム

アルゴリズムはパラメータ `algorithm` によって制御できます。実装された2つのアルゴリズムの結果は一般的に比較できないことに注意してください。

##### 'mean' メソッド

`algorithm == "mean"` の場合、[Girard05](@citet)で提案された方法を選択します。同じ次数の2つのゾノトピック集合 $Z₁$ と $Z₂$ の凸包は、次のように書きます。

$$
Z_j = ⟨c^{(j)}, g^{(j)}_1, …, g^{(j)}_p⟩
$$

ここで $j = 1, 2$ とします。次のように過大評価できます。

$$
CH(Z_1, Z_2) ⊆ \frac{1}{2}⟨c^{(1)}+c^{(2)}, g^{(1)}_1+g^{(2)}_1, …,
g^{(1)}_p+g^{(2)}_p, c^{(1)}-c^{(2)}, g^{(1)}_1-g^{(2)}_1, …, g^{(1)}_p-g^{(2)}_p⟩.
$$

ゾノトープの次数が同じでない場合、このアルゴリズムは `reduce_order` を呼び出して引数の最小値に次数を減らします。

出力されるゾノトープは必ずしも最小の包絡ゾノトープではないことに注意が必要であり、これは高次元では一般的に取得が高コストです。これは[GuibasNZ03](@citet)でさらに調査されています。

##### 'join' メソッド

`algorithm == "join"` の場合、[GhorbalGP09; Definition 1](@citet)で提案された方法を選択します。2つのゾノトピック集合 $Z₁$ と $Z₂$ の凸包 $X$ は、$X$ のボックス近似が $Z₃$ のボックス近似と同一であるようなゾノトープ $Z₃$ によって過大評価されます。$□(X)$ を $X$ のボックス近似とします。$Z₃$ の中心は $□(X)$ の中心です。

生成器の構築は2つのフェーズから成ります。最初のフェーズでは、$Z₁$ からの1つの生成器、例えば $g₁$ と、$Z₂$ からの別の生成器、例えば $g₂$ の組み合わせとして生成器 $g$ を構築します。$g$ の $i$-次元のエントリは次のように与えられます。

$$
    g[i] = \argmin_{\min(g₁[i], g₂[i]) ≤ x ≤ \max(g₁[i], g₂[i])} |x|.
$$

$$
g
$$

がゼロベクトルである場合は、省略できます。

2番目のフェーズでは、各次元のために別の生成器を構築します。これらの生成器はスケーリングされた単位ベクトルです。次の式は、これらの生成器の合計を定義します。

$$
    \sup(□(X)) - c - ∑_g |g|
$$

ここで $c$ は新しいゾノトープの中心であり、$g$s は最初のフェーズで構築された生成器です。 ```
