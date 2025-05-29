```
@test_all ex
@test_all f(args...) key=val ...
@test_all ex broken=true
@test_all ex skip=true
```

式 `all(ex)` が `true` に評価されることをテストします。最初の `false` 値で短絡評価せず、失敗した場合にすべての `false` 要素が表示されるようにします。

[`Test.@test`](@extref Julia) と同様の戻り動作、すなわち：`@testset` 内で実行された場合、`all(ex)` が `true` に評価されると `Pass` `Result` を返し、`false` または `missing` に評価されると `Fail` `Result` を返し、評価できなかった場合は `Error` `Result` を返します。`@testset` の外で実行された場合は、`Fail` または `Error` を返す代わりに例外をスローします。

# 例

```@julia-repl
julia> @test_all [1.0, 2.0] .== [1, 2]
Test Passed

julia> @test_all [1, 2, 3] .< 2
Test Failed at none:1
  Expression: all([1, 2, 3] .< 2)
   Evaluated: false
    Argument: 3-element BitVector, 2 failures:
              [2]: 2 < 2 ===> false
              [3]: 3 < 2 ===> false
```

`@test` と同様に、`@test_all f(args...) key=val...` 形式は `@test_all f(args...; key=val...)` と同等であり、ベクトル化された近似比較のような中置構文を使用する呼び出しが式である場合に便利です：

```@julia-repl
julia> v = [0.99, 1.0, 1.01];

julia> @test_all v .≈ 1 atol=0.1
Test Passed
```

これは、より見栄えの悪いテスト `@test_all .≈(v, 1, atol=0.1)` と同等です。キーワードスプライシングは、任意の否定演算子を通じても機能します：

```@julia-repl
julia> @test_all .!(v .≈ 1) atol=0.001
Test Failed at none:1
  Expression: all(.!.≈(v, 1, atol=0.001))
   Evaluated: false
    Argument: 3-element BitVector, 1 failure:
              [2]: !≈(1.0, 1, atol=0.001) ===> false

```

`@test` と同様に、最初の式が呼び出し（おそらくブロードキャスト `.` 構文）であり、残りが代入（`k=v`）でない限り、複数の式を提供することはエラーです。

このマクロは、`broken=true` および `skip=true` キーワードをサポートしており、[`Test.@test`](@extref Julia) と同様の動作をします：

```@julia-repl
julia> @test_all [1, 2] .< 2 broken=true
Test Broken
  Expression: all([1, 2] .< 2)

julia> @test_all [1, 2] .< 3 broken=true
Error During Test at none:1
 Unexpected Pass
 Expression: all([1, 2] .< 3)
 Got correct result, please change to @test if no longer broken.

julia> @test_all [1, 2, 3] .< 2 skip=true
Test Broken
  Skipped: all([1, 2, 3] .< 2)
```
