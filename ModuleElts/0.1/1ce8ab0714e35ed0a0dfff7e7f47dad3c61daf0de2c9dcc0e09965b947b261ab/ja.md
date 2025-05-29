モジュール要素 – 自由モジュールの要素。

`ModuleElt{K,V}` は、基底要素が型 `K` で、係数が型 `V` の自由モジュールの要素を表します。通常、型 `V` のオブジェクトは（必ずしも可換である必要はない）環の要素であることが望まれますが、アーベル群に属するだけでも有用です。これは、SageMathのCombinatorialFreeModuleに似ています。また、キーが整数ではなく型 `K` である `SparseVector` と考えることもできます。

この基本データ構造は、私のパッケージの多くの場所で効率的な表現として使用されています。例えば、複数変数の単項式を表す型 `Monomial` は `ModuleElt{Symbol,Int}` です：

`x^2y^-3` は `ModuleElt(:x=>2,:y=>-3)` で表されます。

また、複数変数の多項式は、係数の型 `C` を持つ `ModuleElt{Monomial,C}` で表されます：

`x*y-z^2` は `ModuleElt(x*y=>1,z^2=>-1)` で表されます。

`ModuleElts` は、サイクロトミック、CycPol、ヘッケ代数の要素などにも使用されます。

`ModuleElt{K,V}` は本質的に `Pairs{K,V}` のリストです。コンストラクタは、ペアのリスト、可変数のペア引数、またはペアのジェネレータを引数として受け取ります。

2つの実装を提供します：

  * `HModuleElt`、`Dict` による実装

これは、型 `K` がハッシュ可能であることを要求します。これは、型のインターフェースが辞書に近いため非常にシンプルな実装です。唯一の違いは、係数がゼロのキーが破棄されることです。これは、モジュール要素の等価性をチェックするためには、各要素に対して標準形が必要であるためです。

  * `ModuleElt`、キーでソートされたペアのベクターによるより高速な実装。

これは、型 `K` に `isless` メソッドがあることを要求します。この実装は、`Dict` 実装よりも2倍から4倍速く、メモリを半分必要とします。

両方の実装は同じメソッドを持ち、ほとんどが `Dict` と同じメソッドです（`haskey`、`getindex`、`setindex`、`keys`、`values`、`pairs`、`first`、`iterate`、`length`、`eltype`、`copy`）、いくつかの例外があります。要素の追加は、`merge(+,...)` として実装されており、これは `Dict` の `merge` のバリエーションで、操作後に係数ゼロのキーが破棄されます（ここで `+` は、`op(0,x)=op(x,0)=x` の性質を持つ任意の操作に置き換えることができます）。

モジュール要素は、係数に対して定義されている場合、任意の要素（係数に作用）で否定、乗算、または除算（`/` または `//` または `\`）することもできます。引数の順序は尊重され、`V` に対して乗算が可換でない場合に左モジュールと右モジュールを実装することができます。また、`zero` および `iszero` メソッドもあります。

`ModuleElt` には `cmp` および `isless` メソッドがあり、`HModuleElt` にはありません（定義は辞書順です）。また、`ModuleElts.merge2` もあり、これはマージと同じことを行いますが、より一般的な操作に対して有効です。したがって、ゼロ結果のチェックが必要なため、より高価です（私は `min` および `max` とともに使用し、これらは `Monomial` および `CycPol` の `gcd` および `lcm` を実装します）。

ここで例を示します。基底要素は `Symbol` で、係数は `Int` です。例からわかるように、REPL（またはJupyterやPlutoで、`IO` に `:limit` 属性がある場合）では、`show` メソッドが係数（必要に応じて括弧付き、すなわち内部に `+-*/` の出現がある場合）をキーの前に表示します。`repr` メソッドは、Juliaで読み戻すことができる表現を提供します：

```julia-repl
julia> a=ModuleElt(:xy=>1,:yx=>-1)
:xy-:yx

julia> repr(a)
"ModuleElt([:xy => 1, :yx => -1])"

julia> ModuleElt([:xy=>1//2,:yx=>-1])
(1//2):xy+(-1//1):yx
```

`IO` プロパティ `:showbasis` をカスタム印刷関数に設定すると、基底要素の印刷方法が変更されます。

```julia-repl
julia> show(IOContext(stdout,:limit=>true,:showbasis=>(io,s)->string("<",s,">")),a)
3<xy>+2<yx>
```

`ModuleElt` に対する基本操作を示します：

```julia-repl
julia> a-a
0

julia> a*99 # Ints は可換なので 99*a と同じ
99:xy-99:yx

julia> a//2
(1//2):xy+(-1//2):yx

julia> a/2
0.5:xy-0.5:yx

julia> a+ModuleElt(:yx=>1)
:xy

julia> a[:xy] # 基底要素によるインデックスは係数を見つけます
1

julia> a[:xx] # 存在しない基底要素の係数はゼロです。
0

julia> haskey(a,:xx) # !iszero(a[:xx]) と同じ
false

julia> a[:xx]=1 # これは挿入を行います
1

julia> first(a)
:xx => 1

julia> collect(a)
3-element Vector{Pair{Symbol, Int64}}:
 :xx => 1
 :xy => 1
 :yx => -1

julia> collect(keys(a))
3-element Vector{Symbol}:
 :xx
 :xy
 :yx

julia> collect(values(a))
3-element Vector{Int64}:
  1
  1
 -1

julia> length(a)
3

julia> eltype(a)
Pair{Symbol, Int64}
```

両方の実装では、コンストラクタが構築された要素を正規化し、ゼロ係数を削除し、重複する基底要素をマージし、対応する係数を加算します（デフォルトの実装では基底をソートします）。この正規化が不要であることがわかっている場合は、コンストラクタにキーワード `check=false` を渡すことで最大速度のために無効にできます。

```julia-repl
julia> a=ModuleElt(:yy=>1, :yx=>2, :xy=>3, :yy=>-1;check=false)
:yy+2:yx+3:xy-:yy

julia> a=ModuleElt(:yy=>1, :yx=>2, :xy=>3, :yy=>-1)
3:xy+2:yx
```

`ModuleElt` の加算または減算は、必要に応じてキーと係数の型を昇格させます：

```julia-repl
julia> a+ModuleElt([:z=>1.0])
3.0:xy+2.0:yx+1.0:z
```
