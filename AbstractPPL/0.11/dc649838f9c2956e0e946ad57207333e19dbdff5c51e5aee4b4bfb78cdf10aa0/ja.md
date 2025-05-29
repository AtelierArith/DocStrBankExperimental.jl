```
@varname(expr, concretize=false)
```

シンボルまたはインデックス式 `expr` を与えると、[`VarName`](@ref) のインスタンスを返すマクロです。

`concretize` が `true` の場合、結果の式は `concretize()` 呼び出しでラップされます。

動的インデックスを含む式、すなわち `begin` および/または `end` を含む式は、常に具体化する必要があります。`VarName` は `is_static_optic` によって決定される非動的インデックスのみをサポートします。以下に例を示します。

## 例

### 動的インデックス

```jldoctest
julia> x = (a = [1.0 2.0; 3.0 4.0; 5.0 6.0], );

julia> @varname(x.a[1:end, end][:], true)
x.a[1:3, 2][:]

julia> @varname(x.a[end], false)  # 具体化を無効にする
ERROR: LoadError: 変数名 `x.a[end]` は動的であり、具体化が必要です！
[...]

julia> @varname(x.a[end])  # 必要に応じてデフォルトで具体化が行われる
x.a[6]

julia> # ここでの「動的」とは `begin` および/または `end` の使用を指し、
       # _runtimeでのみ利用可能な情報_ ではありません。つまり、以下は機能します。
       [@varname(x.a[i]) for i = 1:length(x.a)][end]
x.a[6]

julia> # 潜在的に驚くべき動作ですが、これは Base が行うことと同等です：
       @varname(x[2:2:5]), 2:2:5
(x[2:2:4], 2:2:4)
```

### 一般的なインデックス

内部では、インデックスに `optic` が使用されています：

```jldoctest
julia> getoptic(@varname(x))
identity (generic function with 1 method)

julia> getoptic(@varname(x[1]))
(@o _[1])

julia> getoptic(@varname(x[:, 1]))
(@o _[Colon(), 1])

julia> getoptic(@varname(x[:, 1][2]))
(@o _[Colon(), 1][2])

julia> getoptic(@varname(x[1,2][1+5][45][3]))
(@o _[1, 2][6][45][3])
```

これは、プロパティアクセスもサポートすることを意味します：

```jldoctest
julia> getoptic(@varname(x.a))
(@o _.a)

julia> getoptic(@varname(x.a[1]))
(@o _.a[1])

julia> x = (a = [(b = rand(2), )], ); getoptic(@varname(x.a[1].b[end], true))
(@o _.a[1].b[2])
```

変数名や配列名には補間を使用できますが、`.` 式の左辺には使用できません。インデックス内の変数は常に呼び出しスコープで評価されます。

```jldoctest
julia> name, i = :a, 10;

julia> @varname(x.$name[i, i+1])
x.a[10, 11]

julia> @varname($name)
a

julia> @varname($name[1])
a[1]

julia> @varname($name.x[1])
a.x[1]

julia> @varname(b.$name.x[1])
b.a.x[1]
```
