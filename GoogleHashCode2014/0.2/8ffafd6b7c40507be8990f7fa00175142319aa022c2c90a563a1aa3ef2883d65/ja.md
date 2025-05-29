```
is_feasible(solution::Solution, city::City; verbose::Bool=false)
```

`solution`が`city`で定義されたインスタンスの制約を満たしているかどうかを確認します。

以下の基準が考慮されます（問題文からの引用）：

  * 旅程の数は`city`の車の数と一致しなければなりません
  * 各旅程の最初の交差点は`city`の出発交差点でなければなりません
  * 旅程の各連続する交差点のペアについて、これらの交差点を接続する通りが`city`に存在しなければなりません（通りが一方向の場合、正しい方向に進む必要があります）
  * 各旅程の所要時間は`city`の総所要時間以下でなければなりません

# 例

```jldoctest
julia> using GoogleHashCode2014, Random

julia> city = read_city();

julia> rng = Random.MersenneTwister(0);

julia> solution = random_walk(rng, city)
Solution with 8 itineraries of lengths [3810, 3277, 3779, 3278, 3451, 3697, 4366, 3707]

julia> is_feasible(solution, city; verbose=false)
true

julia> partial_solution = Solution(solution.itineraries[1:7])
Solution with 7 itineraries of lengths [3810, 3277, 3779, 3278, 3451, 3697, 4366]

julia> is_feasible(partial_solution, city; verbose=false)
false
```
