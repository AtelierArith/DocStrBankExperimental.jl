```
@test_sets L op R
@test_sets L op R broken=true
@test_sets L op R skip=true
```

式 `L op R` が `true` に評価されることをテストします。ここで `op` は集合のような比較として解釈される中置演算子です：

  * `L == R` は `issetequal(L, R)` に展開されます。
  * `L != R` または `L ≠ R` は `!issetequal(L, R)` に展開されます。
  * `L ⊆ R` または `L ⊂ R` は `issubset(L, R)` に展開されます。
  * `L ⊇ R` または `L ⊃ R` は `issubset(R, L)` に展開されます。
  * `L ⊊ R` は `issubset(L, R) && !issetequal(L, R)` に展開されます。
  * `L ⊋ R` は `issubset(R, L) && !issetequal(L, R)` に展開されます。
  * `L ∩ R` または `L || R` は `isdisjoint(L, R)` に展開されます。

[`Test.@test`](@extref Julia) と同様の戻り値の動作、すなわち：`@testset` 内で実行された場合、展開された式が `true` に評価されると `Pass` `Result` を返し、`false` に評価されると `Fail` `Result` を返し、評価できなかった場合は `Error` `Result` を返します。`@testset` の外で実行された場合は、`Fail` または `Error` を返す代わりに例外をスローします。

上記の展開された式で動作する任意の `L` と `R` を使用できます（タプル、配列、集合、辞書、文字列、その他の一般的な反復可能なものを含む）。`∅` シンボルは `Set()` の省略形としても使用できます。

唯一の追加の制限は、`setdiff(L, R)` と `intersect(L, R)` も動作しなければならないことです。これらは、いくつかのケースで情報を提供する失敗メッセージを生成するために使用されます。

参照： [`Base.issetequal`](@extref Julia)、[`Base.issubset`](@extref Julia)、[`Base.isdisjoint`](@extref Julia)、[`Base.setdiff`](@extref Julia)、[`Base.intersect`](@extref Julia)。

!!! note "不交差性"
    最後の形式は、`isdisjoint(L, R)` を `L ∩ R == ∅` と表記する方が良いという点で、表記のわずかな乱用を表しています。このマクロは、この構文をサポートしており、`L ∩ R` および `L || R` の省略形に加えてサポートしています。


!!! note "Unicode 文字の入力"
    Unicode 演算子は、Julia エディタで `\<name><tab>` と書くことで入力できます。このマクロでサポートされている演算子は、`≠` (`\neq`)、`⊆` (`\subseteq`)、`⊇` (`\supseteq`)、`⊂` (`\subset`)、`⊃` (`\supset`)、`⊊` (`\subsetneq`)、`⊋` (`\supsetneq`)、`∩` (`\cap`)、および `∅` (`\emptyset`) です。


# 例

```@julia-repl
julia> @test_sets (1, 2) == (2, 1, 1, 1)
Test Passed

julia> @test_sets ∅ ⊆ 1:5
Test Passed

julia> @test_sets 1:3 ⊇ 5
Test Failed at none:1
  Expression: 1:3 ⊇ 5
   Evaluated: L is not a superset of R.
              R ∖ L has 1 element:  [5]

julia> @test_sets [1, 2, 3] ∩ [2, 3, 4]
Test Failed at none:1
  Expression: [1, 2, 3] ∩ [2, 3, 4] == ∅
   Evaluated: L and R are not disjoint.
              L ∩ R has 2 elements: [2, 3]

julia> @test_sets "baabaa" ≠ 'a':'b'
Test Failed at none:1
  Expression: "baabaa" ≠ 'a':'b'
   Evaluated: L and R are equal.
              L = R has 2 elements: ['b', 'a']
```

このマクロは、`broken=cond` および `skip=cond` キーワードをサポートしており、[`Test.@test`](@extref Julia) と同様の動作をします：

# 例

```@julia-repl
julia> @test_sets [1] ⊆ [2, 3] broken=true
Test Broken
  Expression: [1] ⊆ [2, 3]

julia> @test_sets [1] ⊆ [1, 2] broken=true
Error During Test at none:1
 Unexpected Pass
 Expression: [1] ⊆ [1, 2]
 Got correct result, please change to @test if no longer broken.

julia> @test_sets [1] ⊆ [2, 3] skip=true
Test Broken
  Skipped: [1] ⊆ [2, 3]
```
