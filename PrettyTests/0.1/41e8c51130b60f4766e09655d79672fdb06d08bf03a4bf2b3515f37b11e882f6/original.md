```
@test_sets L op R
@test_sets L op R broken=true
@test_sets L op R skip=true
```

Test that the expression `L op R` evaluates to `true`, where `op` is an infix operator interpreted as a set-like comparison:

  * `L == R` expands to `issetequal(L, R)`
  * `L != R` or `L ≠ R` expands to `!issetequal(L, R)`
  * `L ⊆ R` or `L ⊂ R` expands to `issubset(L, R)`
  * `L ⊇ R` or `L ⊃ R` expands to `issubset(R, L)`
  * `L ⊊ R` expands to `issubset(L, R) && !issetequal(L, R)`
  * `L ⊋ R` expands to `issubset(R, L) && !issetequal(L, R)`
  * `L ∩ R` or `L || R` expands to `isdisjoint(L, R)`

Same return behaviour as [`Test.@test`](@extref Julia), namely: if executed inside a `@testset`, returns a `Pass` `Result` if expanded expression evaluates to `true`, a `Fail` `Result` if it evaluates to `false`, and an `Error` `Result` if it could not be  evaluated. If executed outside a `@testset`, throws an exception instead of returning  `Fail` or `Error`.

You can use any `L` and `R` that work with the expanded expressions above (including  tuples, arrays, sets, dictionaries, strings, and more generable iterables). The `∅`  symbol can also be used as shorthand for `Set()`.

The only additional limitation is that `setdiff(L, R)` and `intersect(L, R)` must also work, since they are used to generate informative failure messages in some cases.

See also: [`Base.issetequal`](@extref Julia), [`Base.issubset`](@extref Julia), [`Base.isdisjoint`](@extref Julia), [`Base.setdiff`](@extref Julia),  [`Base.intersect`](@extref Julia).

!!! note "Disjointness"
    The last form represents a slight abuse of notation, in that `isdisjoint(L, R)` is better notated as `L ∩ R == ∅`. The macro also supports this syntax, in addition  to shorthand `L ∩ R` and `L || R`.


!!! note "Typing unicode characters"
    Unicode operators can be typed in Julia editors by writing  `\<name><tab>`. The ones supported by this macro are `≠` (`\neq`),  `⊆` (`\subseteq`), `⊇` (`\supseteq`), `⊂` (`\subset`), `⊃` (`\supset`),  `⊊` (`\subsetneq`), `⊋` (`\supsetneq`), `∩` (`\cap`), and `∅` (`\emptyset`).


# Examples

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

The macro supports `broken=cond` and `skip=cond` keywords, with similar behavior  to [`Test.@test`](@extref Julia):

# Examples

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
