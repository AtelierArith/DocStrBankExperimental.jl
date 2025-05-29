```julia
    laplacian(Δ²::𝕃{S}, epsilon::Real=0;
              <densityInvariant=false>) where S<:Real
```

与えられた `LowerTriangular` 行列の二乗間距離 $Δ^2$ に対して、いわゆる *正規化ラプラシアン* または *密度不変正規化ラプラシアン* の下三角部分を返します。いずれの場合も、これは対称ラプラシアンです。ラプラシアンの要素は $Δ^2$ の要素と同じ型です。結果は `LowerTriangular` 行列です。

Lafon (2004)[🎓](@ref) によって定義されたラプラシアンが実装されています：

まず、すべての $Δ^2$ の要素に対して [ガウス放射基底関数](https://bit.ly/1HVyf55)、すなわち *ガウスカーネル* または *ヒートカーネル* が適用されます。

$$
W_{ij} = exp\bigg(\frac{\displaystyle{-Δ^2_{ij}}}{\displaystyle{2ε}}\bigg)
$$

,

ここで $ε$ はカーネルの *バンド幅* です。

<オプションのキーワード引数> `densityInvariant=true` が使用されると、密度不変変換が適用されます。

$$
W \leftarrow E^{-1}WE^{-1}
$$

ここで $E$ は、$W$ の行（または列）の合計を主対角線に持つ対角行列です。

最後に、正規化ラプラシアン（密度不変かどうかにかかわらず）は次のように定義されます。

$$
Ω = D^{-1/2}WD^{-1/2}
$$

,

ここで $D$ は、$W$ の行（または列）の合計を主対角線に持つ対角行列です。

引数 `epsilon` を提供しない場合、バンド幅 $ε$ は二乗距離行列 $Δ^2_{ij}$ の要素の中央値に設定されます。もう一つの推測は、元のデータの次元、すなわち二乗距離行列を計算するために使用されたデータの次元です。正定値行列の場合、これは $n(n-1)/2$ であり、ここで $n$ は行列の次元です。さらに、次の [`spectralEmbedding`](@ref) 空間の次元も考慮されます。`epsilon` パラメータ（正でなければならない）を調整することで、埋め込み空間の圧縮率と埋め込み空間内の点の広がりの両方を制御できることに注意してください。$ε$ に関する議論は Coifman et *al.* (2008)[🎓](@ref) を参照してください。

!!! note "Nota Bene"
    ここで定義されたラプラシアンは、スカラーや適切なメトリックを使用してベクトル上で得られた二乗間距離の入力行列に対して要求できます。いずれにせよ、ラプラシアンの下三角部分のみが入力として取られます。 [行列の型キャスト](@ref) を参照してください。


**関連項目**: [`distanceSqrMat`](@ref), [`laplacianEigenMaps`](@ref), [`spectralEmbedding`](@ref).

**例**

```julia
using PosDefManifold
# 4つのランダムな10x10 SPD行列のセットを生成
Pset=randP(10, 4) # または、ユニコードを使用して: 𝐏=randP(10, 4)
Δ²=distanceSqrMat(Fisher, Pset)
Ω=laplacian(Δ²)

# 密度不変ラプラシアン
Ω=laplacian(Δ²; densityInvariant=true)

# バンド幅を増加させる
r=size(Δ², 1)
myεFactor=0.1
med=Statistics.median([Δ²[i, j] for j=1:r-1 for i=j+1:r])
ε=2*myεFactor*med
Ω=laplacian(Δ², ε; densityInvariant=true)
```
