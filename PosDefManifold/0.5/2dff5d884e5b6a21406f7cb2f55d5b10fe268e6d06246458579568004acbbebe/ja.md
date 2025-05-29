```
    (1) randPosDefMat(n::Int;
    <
    df::Int=2,
    eigvalsSNR::Real=10e3 >)

    (2) randPosDefMat(::Type{Complex{T}}, n:: Int;
    < 同じキーワード引数が(1)と同じ >)

    (3) randPosDefMat(n::Int, k::Int;
    <
    df::Int=2,
    eigvalsSNR::Real=10e3,
    SNR::Real=100,
    commuting=false >)

    (4) randPosDefMat(::Type{Complex{T}}, n::Int, k::Int;
    < 同じキーワード引数が(3)と同じ >)
```

**エイリアス**: `randP`

生成

  * (1) サイズ $n⋅n$ のランダムな `Hermitian` 正定値行列 (実数)
  * (2) サイズ $n⋅n$ のランダムな `Hermitian` 正定値行列 (複素数)
  * (3) (1)の種類の $k$ 行列の 1次元配列 ([ℍVector type](@ref))
  * (4) (2)の種類の $k$ 行列の 1次元配列 ([ℍVector type](@ref)).

メソッド (3) と (4) は **マルチスレッド** です。 [Threads](@ref) を参照してください。

(1) と (2) の場合、行列はモデルに従って生成されます

$$
UΛU^H+ηI
$$

,

ここで $U$ は関数 `randU` ([`randUnitaryMat`](@ref)) によって生成されたランダムな直交行列 (1) またはユニタリ行列 (2) であり、$Λ$、$η$ は正定値対角行列と *<オプションのキーワード引数>* `df` と `eigvalsSNR` に依存する非負スカラーで、関数 `randΛ` ([`randEigvalsMat`](@ref)) を呼び出してランダムに生成されます。

(3) と (4) の場合、*<オプションのキーワード引数>* `commuting=true` が渡されると、$k$ 行列はモデルに従って生成されます

$$
UΛ_iU^H+ηI,\hspace{8pt}
$$

, ただし $i$=1:$k$

そうでない場合、次のモデルに従って生成されます

$$
(UΛ_iU^H+ηI)+φ(V_iΔ_iV_i^H+ηI),\hspace{8pt}
$$

, ただし $i$=1:$k$  Eq.[1]

ここで

  * $$
    U
    $$

    と $V_i$ はランダムな (3) 直交/(4) ユニタリ行列です、
  * $$
    Λ_i
    $$

    と $Δ_i$ は正定値対角行列です
  * $$
    η
    $$

    は非負スカラーです。

ここでのすべての変数は (1) と (2) のようにランダムに生成されます

  * $$
    φ
    $$

    は所望の出力 `SNR` ([信号対雑音比](https://bit.ly/1VvpvnQ)) を得るために調整されます。これはまた

*<オプションのキーワード引数>* であり、次のようになります

$$
SNR=\frac{\displaystyle\sum_{i=1}^{k}\textrm{tr}(UΛ_iU^H+ηI)}{\displaystyle\sum_{i=1}^{k}\textrm{tr}φ(V_iΔ_iV_i^H+ηI)}
$$

.

!!! note "Nota Bene"
    キーワード引数 `SNR` はデシベルで表現されるのではなく、期待される SNR 分散比として表現されます。正の数でなければなりません。


正定値行列を生成するためのこのモデルのわずかに異なるバージョンが (Congedo et *al.*, 2017b)[🎓] で提案されています; Eq. [1] のモデルでは

  * $$
    UΛ_iU^H
    $$

    は信号項であり、信号はすべての行列で同じ座標を共有すると仮定されています、
  * $$
    φ(V_iΔ_iV_i^H)
    $$

    は構造化された雑音項であり、すべての行列で異なります
  * $$
    ηI
    $$

    はすべての行列で同じ分散を持つ [ホワイトノイズ](https://bit.ly/2TN8472) 項です。

**参照**: 前述の論文と `randΛ` ([`randEigvalsMat`](@ref))。

**例**

```julia
using PosDefManifold
R=randP(10, df=10, eigvalsSNR=1000) # サイズ 10x10 の 1 SDP 行列 #(1)
H=randP(ComplexF64, 5, eigvalsSNR=10) # サイズ 5x5 の 1 Hermitian 行列 # (2)
ℛ=randP(10, 1000, eigvalsSNR=100) # サイズ 10x10 の 1000 SPD 行列 # (3)
using Plots
heatmap(Matrix(ℛ[1]), yflip=true, c=:bluesreds)
ℋ=randP(ComplexF64, 20, 1000) # サイズ 20x20 の 1000 Hermitian 行列 # (4)
```
