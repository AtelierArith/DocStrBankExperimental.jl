```
@testset_macro @mac
```

`@mac`をマクロとして宣言し、`retest`によって静的に展開される必要があるため、含まれる`@testset`を発見できるようにします。

次のパターンを考えてみましょう。これは関数内でテストセットを分離する`Test`を使用しています：

```julia
using Test

function test_iseven(x)
    @testset "iseven $x" begin
        @test iseven(x)
    end
end

@testset "test $x" for x=2:2:4
    test_iseven(x)
end
```

これは`ReTest`では直接翻訳できません。なぜなら、`test_iseven`の呼び出しは実行時に行われ、新しい`@testset "iseven $x"`がトップレベルで宣言されることになるからです（これはテストセット内に`include`を持つことに似た問題です）。したがって、`retest()`の最初の実行では`@test`は実行されず、2回目の実行では`x`がグローバルスコープで定義されていないため失敗します。

代替案は、`test_iseven`をマクロに変え、`@testset_macro`で宣言することです：

```julia
using ReTest

macro test_iseven(x)
    quote
        @testset "iseven $($x)" begin
            @test iseven($x)
        end
    end
end

@testset_macro @test_iseven

@testset "test $x" for x=2:2:4
    @test_iseven(x)
end
```

その後、`retest("iseven", verbose=2)`を実行すると、次のようになります：

```
                    Pass
test 2          |      1
  iseven 2      |      1
test 4          |      1
  iseven 4      |      1
Main            |      2
```
