```
    (1) randEigvalsMat(n::Int;
    <
    df::Int=2,
    eigvalsSNR::Real=10e3 >)

    (2) randEigvalsMat(n::Int, k::Int;
    < (1) と同じキーワード引数 >)
```

**エイリアス**: `randΛ`

(1) ランダムな実正の固有値を持つ $n⋅n$ 対角行列を生成します。

(2) (1) の種類の $k$ 行列の 1d 配列（[𝔻Vector 型](@ref)）

固有値は次のモデルに従って生成されます。

$$
λ_i=χ_{df}^2+η,\hspace{6pt}\textrm{for}\hspace{2pt}i=1:n,
$$

ここで

  * $$
    χ_{df}^2
    $$

    （信号項）は `df` 自由度の [カイ二乗分布](https://bit.ly/1IXkulE) に従ってランダムに分布します。
  * $$
    η
    $$

    は *<キーワード引数>* `eigvalsSNR` の関数である [ホワイトノイズ](https://bit.ly/2TN8472) 項であり、次のようになります。

$$
\textrm{固有値 SNR}=\mathbb{E}\big(\sum_{i=1}^{n}λ_i\big)\big/nη.
$$

ここでの期待値の合計 $\mathbb{E}\big(\sum_{i=1}^{n}λ_i\big)$ は信号項の期待分散、すなわち $n(df)$ であり、ランダムなカイ二乗変数の期待値はその自由度に等しいためです。

引数として `eigvalsSNR=Inf` が渡されると、$η$ はゼロに設定され、*すなわち* ホワイトノイズは追加されません。いずれにせよ `eigvalsSNR` は正でなければなりません。

デフォルト値の *<キーワード引数>* `df` (`df=2`) では、生成モデルは固有値が指数的に減衰する分散を持つと仮定しており、これは実データでよく観察されます。

!!! 注 "Nota Bene"     *<キーワード引数>* `eigvalsSNR` は期待される固有値 SNR（[信号対雑音比](https://bit.ly/1VvpvnQ））を表し、実際のものではなく、デシベルで表されず、期待される SNR 分散比として表されます。

この関数は、関数 `randP` （[`randPosDefMat`](@ref)）によって使用され、実データで観察される固有値を模倣し、生成された行列の逆行列に関する条件を改善するために、ホワイトノイズを追加したランダムな正定値行列を生成します。

**関連項目**: `randλ` （[`randEigvals`](@ref)）、`randU` （[`randUnitaryMat`](@ref)）、`randP` （[`randPosDefMat`](@ref)）、`randχ²` （[`randChi²`](@ref)）。

**例**

```julia
using PosDefManifold
# (1)
n=3;
U=randU(n);
Λ=randΛ(n, eigvalsSNR=100)
P=U*Λ*U' # SPD 行列を生成
using LinearAlgebra
Q=ℍ(U*Λ*U') # SPD 行列を生成し、'Hermitian' としてフラグを立てる

# (2) シミュレートされた固有値の行列の配列を 10 個生成
Dvec=randΛ(n, 10)
```
