```julia
function fisherExactMcTest(<same args and kwargs as `chiSquaredMcTest`>)
```

実際には[`chiSquaredMcTest`](@ref)のエイリアスです。2x2のコンティンジェンシーテーブルに使用できます。詳細については[`chiSquaredTest`](@ref)を参照してください。

*単変量バージョン:* [`fisherExactTest`](@ref)

[MultcompTest](@ref)構造体を返します。

*例*

```julia
using PermutationTests
tables=[[6 1; 2 5], [4 1; 4 5], [5 2; 3 4]];
tR=fisherExactMcTest(tables; direction=Right()) 
# または tR=Χ²Test(tables; direction=Right())
```
