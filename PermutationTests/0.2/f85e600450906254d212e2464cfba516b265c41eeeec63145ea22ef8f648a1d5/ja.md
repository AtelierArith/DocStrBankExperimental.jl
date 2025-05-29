```julia
function chiSquaredMcTest(tables::AbstractVector{Matrix{I}};
            direction::TestDir = Both(),
            switch2rand::Int = max(Int(1e8) ÷ length(𝐘), Int(1e4)), 
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true,            
            #
            stepdown::Bool = true,
            fwe::Float64 = 0.05,
            threaded::Bool = Threads.nthreads()>=4,
            asPearson::Bool = true) 
                    where {I <: Int, TestDir <: TestDirection}
```

複数比較の[カイ二乗](https://en.wikipedia.org/wiki/Chi-squared_test) ($\chi^2$) パーミュテーションテストは、$2 \cdot K$ のコンティンジェンシーテーブルに対して行われ、ここで $K$ は ≥2 です。これは、同じ次元と同じ列の合計を持つ $M$ のコンティンジェンシーテーブルを同時にテストします。

$$
M
$$

の帰無仮説は次の形を持ちます。

$$
H_0(m): O_m=E_m
$$

, \quad m=1...M``,

ここで $O_m$ と $E_m$ は $m^{th}$ コンティンジェンシーテーブルの観測頻度と期待頻度です。

`tables` は $M$ のコンティンジェンシーテーブルのベクトルです。詳細については [`chiSquaredTest`](@ref) を参照してください。

オプションのキーワード引数 `direction`、`switch2rand`、`nperm`、`seed`、`verbose`、`stepdown`、`fwe` および `threaded` については [こちら](@ref "Common kwargs for multiple comparisons tests") を参照してください。

$$
K=2
$$

の場合、この関数は [`studentMcTestIS`](@ref) を呼び出し、引数 `asPearson` も渡します。それ以外の場合は [`anovaMcTestIS`](@ref) を呼び出し、引数 `asPearson` は無視されます。

*方向性テスト、パーミュテーションスキームおよび正確なテストのためのパーミュテーション数:* *単変量バージョン* [`chiSquaredTest`](@ref) に従います。

*エイリアス:* `Χ²McTest`、[`fisherExactMcTest`](@ref)

[MultcompTest] 構造体を返します。

!!! warning
    $$
    K>2
    $$

    の場合、二項テーブルのパーミュテーションは帰無の「平方和内」を生成する可能性があり、そのため ANOVA の無限の *F* 統計量をもたらすことがあります。この場合、返された構造体の `.nulldistr` フィールドにはいくつかの julia `Inf` 要素が含まれます。これは、単変量バージョンのテスト ([`chiSquaredTest`](@ref)) には適用されず、この場合は ANOVA のための同等の統計量が使用されます（[Statistic](@ref) を参照）ので、これらの統計量は決して無限にはなりません。


*例*

```julia
using PermutationTests
tables=[[3 3 2; 0 0 1], [1 2 2; 2 1 1], [3 1 2; 0 2 1]];
t=Χ²McTest(tables) # テストは双方向です

tables=[[6 1; 2 5], [4 1; 4 5], [5 2; 3 4]]
tR=fisherExactMcTest(tables; direction=Right()) 
# または tR=Χ²Test(tables; direction=Right())

# PearsonR 統計量を使用しない
tR_=fisherExactMcTest(tables; direction=Right(), asPearson=false) 

```
