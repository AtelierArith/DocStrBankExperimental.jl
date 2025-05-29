```julia
function mcNemarMcTest(same args and kwargs as `cochranqMcTest`>)
```

実際には [cochranqMcTest](@ref) のエイリアスです。

$$
M
$$

個の McNemar テストを同時に実行します。

入力 `tables` は、サイズ $Nx2$ のゼロと一の $M$ 個のテーブルのベクトルであり、$N$ は観測数、$2$ は繰り返し測定の数です。詳細については [`cochranqTest`](@ref) を参照してください。

*単変量バージョン:* [`mcNemarTest`](@ref)

[MultcompTest](@ref) 構造体を返します。

*例*

```julia
using PermutationTests
tables=[[1 1; 1 0; 1 0; 0 0; 1 0; 1 0],
        [1 0; 1 1; 1 0; 0 1; 0 0; 1 0],
        [0 1; 0 0; 1 0; 1 0; 1 0; 1 1]];
t=mcNemarMcTest(tables) # デフォルトではテストは双方向です

tR=mcNemarMcTest(tables; direction=Right()) # 右方向のテスト
```
