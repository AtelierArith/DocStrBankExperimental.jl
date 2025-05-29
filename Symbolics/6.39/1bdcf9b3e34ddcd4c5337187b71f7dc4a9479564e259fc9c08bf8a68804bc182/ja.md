```
symbolic_solve(expr, x; dropmultiplicity=true, warns=true)
```

`symbolic_solve` は、さまざまな方法を使用して入力された方程式/式を象徴的に解こうとする関数です。

## 引数

  * expr: 単一の単変数式（多項式の形）または複数の単変数式、または複数の多変数多項式、または超越的非線形関数である可能性があります。
  * x: 解くべき単一の変数または変数の配列
  * dropmultiplicity (オプション): 出力を根の出現回数 `n` 回印刷するべきか？例えば、`(x+1)^2` がある場合、2つの根 `x = -1` があり、デフォルトでは出力は `[-1]` です。dropmultiplicity が false と入力された場合、出力は `[-1, -1]` になります。
  * warns (オプション): 無効な式やケースが入力された場合、何も返す前にソルバーがそのようなケースについて警告すべきか？これが false に設定されている場合、ソルバーは何も返しません。デフォルトでは、warns は true に設定されています。

## サポートされている入力

基本ソルバー（`symbolic_solve`）は、入力のタイプ（複数/単一変数および複数/単一式）に応じて選択する複数のソルバーを持っており、入力が有効であることを確認した後にのみ使用されます。

入力された式にはパラメータが含まれる場合があり、これらは超越的であると仮定されます。パラメータ "a" は、P(a) = 0 となる有理係数の多項式 P が存在しない場合に超越的です。例のセクションを確認してください。

現在、`symbolic_solve` は以下をサポートしています。

  * 線形および多項式方程式（パラメータ付き）
  * 線形および多項式方程式の系（今のところ追加のパラメータなし）
  * 超越関数を含む方程式（パラメータ付き）

## 例

### `solve_univar`（因数分解と解析的解法を使用して4次まで）

!!! note
    `solve_univar` および `solve_multipoly` を使用するには、パッケージ `Nemo` が必要です。次の例で見るように `using Nemo` を実行することが必要です。そうしないと、関数はエラーをスローします。


```jldoctest
julia> using Symbolics, Nemo;

julia> @variables x a b;

julia> expr = expand((x + b)*(x^2 + 2x + 1)*(x^2 - a))
-a*b - a*x - 2a*b*x - 2a*(x^2) + b*(x^2) + x^3 - a*b*(x^2) - a*(x^3) + 2b*(x^3) + 2(x^4) + b*(x^4) + x^5

julia> symbolic_solve(expr, x)
4-element Vector{Any}:
 -1
   -b
   (1//2)*√(4a)
   (-1//2)*√(4a)

julia> symbolic_solve(expr, x, dropmultiplicity=false)
5-element Vector{Any}:
 -1
 -1
   -b
   (1//2)*√(4a)
   (-1//2)*√(4a)
```

```jldoctest
julia> symbolic_solve(x^2 + a*x + 6, x)
2-element Vector{SymbolicUtils.BasicSymbolic{Real}}:
 (1//2)*(-a + √(-24 + a^2))
 (1//2)*(-a - √(-24 + a^2))
```

```jldoctest
julia> symbolic_solve(x^7 - 1, x)
2-element Vector{Any}:
  roots_of((1//1) + x + x^2 + x^3 + x^4 + x^5 + x^6, x)
 1
```

### `solve_multivar`（Groebner 基底と `solve_univar` を使用して根を見つける）

!!! note
    `solve_univar` と同様に、`solve_multivar` が完全に機能するためには `Groebner` が必要です。


```jldoctest
julia> using Groebner

julia> @variables x y z
3-element Vector{Num}:
 x
 y
 z

julia> eqs = [x+y^2+z, z*x*y, z+3x+y]
3-element Vector{Num}:
 x + z + y^2
       x*y*z
  3x + y + z

julia> symbolic_solve(eqs, [x,y,z])
3-element Vector{Any}:
 Dict{Num, Any}(z => 0, y => 1//3, x => -1//9)
 Dict{Num, Any}(z => 0, y => 0, x => 0)
 Dict{Num, Any}(z => -1, y => 1, x => 0)
```

!!! note
    必要なときに `Nemo` または `Groebner` がインポートされていない場合、ソルバーはエラーをスローします。


```jldoctest
julia> using Symbolics

julia> @variables x y z;

julia> symbolic_solve(x+1, x)
ERROR: "Nemo is required. Execute `using Nemo` to enable this functionality."

julia> symbolic_solve([x+1, y], [x, y])
ERROR: "Groebner bases engine is required. Execute `using Groebner` to enable this functionality."
```

### `solve_multipoly`（入力多項式間のGCDを使用）

```jldoctest
julia> symbolic_solve([x-1, x^3 - 1, x^2 - 1, (x-1)^20], x)
1-element Vector{BigInt}:
 1
```

### `ia_solve`（隔離と引き寄せによる解法）

```jldoctest
julia> symbolic_solve(2^(x+1) + 5^(x+3), x)
1-element Vector{SymbolicUtils.BasicSymbolic{Real}}:
 (-slog(2) - log(complex(-1)) + 3slog(5)) / (slog(2) - slog(5))
```

```jldoctest
julia> symbolic_solve(log(x+1)+log(x-1), x)
2-element Vector{SymbolicUtils.BasicSymbolic{BigFloat}}:
 (1//2)*√(8.0)
 (-1//2)*√(8.0)
```

```jldoctest
julia> symbolic_solve(a*x^b + c, x)
((-c)^(1 / b)) / (a^(1 / b))
```

### 出力の評価（浮動小数点数への変換）

`symbolic_solve` によって見つかった正確な式を評価したい場合、次のようにできます。

```jldoctest
julia> roots = symbolic_solve(2^(x+1) + 5^(x+3), x)
1-element Vector{SymbolicUtils.BasicSymbolic{Real}}:
 (-slog(2) - log(complex(-1)) + 3slog(5)) / (slog(2) - slog(5))

julia> Symbolics.symbolic_to_float.(roots)
1-element Vector{Complex{BigFloat}}:
 -4.512941594732059759689023145584186058252768936052415430071569066192919491762214 + 3.428598090438030380369414618548038962770087500755160535832807433942464545729382im
```
