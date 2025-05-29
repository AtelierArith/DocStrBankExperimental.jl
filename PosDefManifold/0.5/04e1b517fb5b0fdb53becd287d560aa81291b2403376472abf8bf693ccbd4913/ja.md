```julia
    (1) means(metric::Metric, 𝒫::ℍVector₂;
    <⏩=true>)

    (2) means(metric::Metric, 𝒟::𝔻Vector₂;
    <⏩=true>)
```

(1) 正定行列の2次元配列$𝒫$を[ℍVector₂型](@ref)として与えられた場合、指定された`metric`の[Metric::列挙型](@ref)を使用して、$𝒫$に含まれる[ℍVector型](@ref)オブジェクトの数だけ[Fréchet平均](@ref)を計算します。平均値は`Hermitian`行列のベクトルとして、すなわち`ℍVector`型として返されます。

(2) 実数の正定行列の2次元配列$𝒟$を[𝔻Vector₂型](@ref)として与えられた場合、指定された`metric`の[Metric::列挙型](@ref)を使用して、$𝒟$に含まれる[𝔻Vector型](@ref)オブジェクトの数だけ[Fréchet平均](@ref)を計算します。平均値は`Diagonal`行列のベクトルとして、すなわち`𝔻Vector`型として返されます。

加重Fréchet平均はこの関数ではサポートされていません。

`⏩=true`（デフォルト）の場合、平均の計算はマルチスレッドで行われます。

!!! note "Nota Bene"
    [マルチスレッド](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1)は、Juliaが1つのスレッドのみを使用するように指示された場合、自動的に無効になります。[Threads](@ref)を参照してください。


**関連情報**: [`mean`](@ref).

**例**

```julia
using PosDefManifold
# 4つのランダムな3x3 SPD行列のセットを生成
Pset=randP(3, 4) # または、ユニコードを使用して: 𝐏=randP(3, 4)
# 40のランダムな4x4 SPD行列のセットを生成
Qset=randP(3, 40) # または、ユニコードを使用して: 𝐐=randP(3, 40)
# 直接ℍVectorオブジェクトをリストする
means(logEuclidean, ℍVector₂([Pset, Qset])) # または: means(logEuclidean, ℍVector₂([𝐏, 𝐐]))
# [𝐏, 𝐐]は実際にはℍVector₂型オブジェクトであることに注意

# ℍVector₂型のオブジェクトを作成して渡す
sets=ℍVector₂(undef, 2) # または: 𝒫=ℍVector₂(undef, 2)
sets[1]=Pset # または: 𝒫[1]=𝐏
sets[2]=Qset # または: 𝒫[2]=𝐐
means(logEuclidean, sets) # または: means(logEuclidean, 𝒫)

# マルチスレッドでの実行

# まず、200の50x50 SPD行列のセットを20作成
sets=ℍVector₂([randP(50, 200) for i=1:20])

# どれだけ計算時間を節約できるか？
# （4スレッドと4 BLASスレッドで得られた最小時間の例）
using BenchmarkTools

# 非マルチスレッド、閉じた形式の解を持つ平均
@benchmark(means(logEuclidean, sets; ⏩=false)) # (6.196 s)

# マルチスレッド、閉じた形式の解を持つ平均
@benchmark(means(logEuclidean, sets)) # (1.897 s)

sets=ℍVector₂([randP(10, 200) for i=1:10])

# 非マルチスレッド、反復解を持つ平均
# 少し待つ
@benchmark(means(Fisher, sets; ⏩=false)) # (4.672 s )

# マルチスレッド、反復解を持つ平均
@benchmark(means(Fisher, sets)) # (1.510 s)
```
