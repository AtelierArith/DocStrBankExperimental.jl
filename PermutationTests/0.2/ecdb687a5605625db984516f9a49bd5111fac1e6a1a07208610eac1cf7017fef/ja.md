```julia
function cochranqMcTest(tables::AbstractVector{Matrix{I}};
            direction::TestDir = Both(),
            switch2rand::Int = max(Int(1e8) ÷ length(𝐘), Int(1e4)),
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true,
            #
            stepdown::Bool = true,
            fwe::Float64 = 0.05,
            threaded::Bool = Threads.nthreads()>=4) 
                where {I <: Int, TestDir <: TestDirection}
```

データの置換による複数比較 [Cochran Q](https://en.wikipedia.org/wiki/Cochran's_Q_test)。

Cochran Q テストは、繰り返し測定のための1-way ANOVAに類似していますが、二項データ（ゼロと1）を入力として受け取ります。$M$ 個の仮説があり、それぞれが $N$ の観察単位（例：*被験者*、*ブロック*など）と $K$ の繰り返し測定（例：*処置*、*時間*など）で構成されている場合、帰無仮説は次の形を持ちます。

$$
H_0(m): μ_{m1}= \ldots =μ_{mk}, \quad m=1...M
$$

、

ここで $μ_{mk}$ は $k^{th}$ 処置の平均です。

入力 `tables` は、サイズ $NxK$ のゼロと1の $M$ 個のテーブルのベクトルであり、$N$ は観察の数、$K$ は繰り返し測定です。詳細については [`cochranqTest`](@ref) を参照してください。

オプションのキーワード引数 `direction`、`switch2rand`、`nperm`、`seed`、`verbose`、`stepdown`、`fwe` および `threaded` については [こちら](@ref "Common kwargs for multiple comparisons tests") を参照してください。

*方向性テスト、置換スキームおよび正確なテストのための置換の数:* *単変量バージョン* [`cochranqTest`](@ref) に従って

*エイリアス:* `qMcTest`、[`mcNemarMcTest`](@ref)

[MultcompTest](@ref) 構造体を返します。

*例*

```julia
using PermutationTests
tables=[ [1 1 0; 1 0 0; 1 1 1; 1 1 0; 1 0 1; 1 1 0],
        [1 0 0; 1 1 0; 1 1 0; 1 1 1; 1 0 0; 1 0 0],
        [1 0 0; 0 0 1; 1 0 1; 1 1 0; 1 0 1; 1 0 0]];
t=qMcTest(tables) # K>2 のテストは双方向のみ可能
```
