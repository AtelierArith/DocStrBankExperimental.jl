```julia
    (1) inductiveMean(metric::Metric, 𝐏::ℍVector)

    (2) inductiveMean(metric::Metric, 𝐏::ℍVector, q::Int, Q::ℍ)
```

**エイリアス**: `indMean`

(1) 大数の法則に基づく帰納的手法を用いて、[ℍVector type](@ref) の $k$ 個の正定値行列の 1d 配列 $𝐏={P_1,...,P_k}$ のフレシェ平均を計算します (Ho et *al.,* 2013; Lim and Palfia, 2019; Massart et *al.*, 2018)[🎓](@ref)。例えば、

$$
G_1=P_1,
$$

$$
G_i=γ(i^{-1}, G_{(i-1)}, P_i), i=2,...,k,
$$

ここで $γ(i^{-1}, G_{(i-1)}, P_i)$ は、指定された `metric` を使用して、アーク長 $i^{-1}$ で $G_{(i-1)}$ から $P_i$ への [測地線](@ref) 上のステップです。タイプは [Metric::Enumerated type](@ref) です。

(2) (1) と同様ですが、行列の集合 $𝐐 ∪ 𝐏$ に対して、$𝐏$ の集合のみの知識があると仮定し、$𝐐$ の平均（エルミート行列引数 `Q`）と $𝐐$ の行列の数（整数引数 `q`）を考慮します。このメソッドは、例えば、$𝐏$ が到着ブロックで、`Q` が前の平均推定、`q` がオンラインで平均が計算された行列の累積数であるブロックオンラインアルゴリズムの更新に使用できます。

閉じた形の表現を持たないフレシェ平均に対して、この手法は勾配降下法または不動点アルゴリズムの2回未満の反復に相当する計算複雑性を特徴とします。これは近似の代償を伴います。実際、解は配列 𝐏 内の行列の順列に対して不変ではなく、有限サンプルに対するフレシェ平均への収束は保証されません（Lim and Palfia, 2019; Massart et *al.*, 2018)[🎓](@ref) を参照）。

帰納的平均は [`geodesic`](@ref) 関数を使用するため、フォン・ノイマン距離には利用できません。

**例**

```julia
# 平均を計算したい行列のセット 100 個
𝐏=randP(10, 100)

𝐏1=ℍVector(collect(𝐏[i] for i=1:50)) # 最初の 50
𝐏2=ℍVector(collect(𝐏[i] for i=51:100)) # 最後の 50

# 全体のセット 𝐏 の帰納的平均
G=inductiveMean(Fisher, 𝐏)

# 通常の勾配降下法アルゴリズムを使用した平均
H, iter, conv=geometricMean(𝐏)

# 𝐏2 のみが与えられた場合の 𝐏 の帰納的平均、
# 𝐏1 の行列の数と 𝐏1 の平均
G2=inductiveMean(Fisher, 𝐏2, length(𝐏1), mean(Fisher, 𝐏1))

# 平均誤差
norm(G-H)/(dim(G, 1)^2)
norm(G2-H)/(dim(G, 1)^2)
```
