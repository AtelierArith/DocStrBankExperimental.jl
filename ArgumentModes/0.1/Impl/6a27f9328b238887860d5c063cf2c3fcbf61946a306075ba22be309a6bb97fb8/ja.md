```
struct Mode
```

`Mode` は `Val` の拡張として見ることができ、関数引数の型として使用されることを意図しています。その意味は、メソッドディスパッチ中に考慮されるシンボル（フラグ）の集合です。`Mode` の特化は、関数メソッドが引数として受け入れるシンボルのリストを宣言することを可能にします。シンボルには、指定された型の追加パラメータが付随することがあります。

この型のメカニズムについての詳細な説明は以下の通りです。特化された `Mode` 型 **M=Mode[s₁⇒t₁, s₂⇒t₂, ...]** は、型 `Symbol` のシンボルのコレクション **s₁**, **s₂**, ... と、対応する型 **t₁**, **t₂**, ...（型 `DataType` または `DataType` の `Union`）によって決定されます。`Mode` のインスタンス **m::Mode** は、さらに各 **sᵢ** の型 **tᵢ** に対する値 **vᵢ** を含みます。**param(x)** は、コレクション **{sᵢ=>tᵢ}ᵢ** を示します（ここで **x** は `Mode` のインスタンスまたは特化型です）。したがって、**m** は **M** の型であるのは、**param(m) ⊆ param(M)** の場合のみです。これにより、ディスパッチは **param(m)** に基づいて関数の適切なメソッドを選択することができます。

参照: [`checkmode`](@ref)

# 型特化のコンストラクタ

```
Mode[ s₁ [=> t₁] [, s₂ [=> t₂]]... ]
```

特化 **M=Mode[s₁⇒t₁, s₂⇒t₂, ...]** を構築し、関数メソッド宣言の引数の型として使用します。型 **M** の引数は、**param(m) ⊆ param(M)** を満たすインスタンス **m::Mode** のみを受け入れます。型宣言において、いくつかまたはすべての **tᵢ** が省略されることがあり、その場合は `Nothing` がデフォルトとなります。例: `Mode[:a, :b => Int, :c => Tuple{Int, String}]`。

シンボル `==` も、具体的な型が必要であることを示すためにコンストラクタ呼び出しの最初の引数として追加できます（上記のように `UnionAll` ではなく）。このオプションは補助的な目的のためにのみ追加され、一般的には有用ではないはずです。

このような非慣習的な構文（ブラケット `[`,`]` を使用）は、型宣言のコードが関数シグネチャ内の型名の提示に似て見えるようにするために使用されていることに注意してください。

# インスタンスのコンストラクタ

```
Mode( s₁[=> v₁] [, s₂ [=> v₂]]... )
```

値 **v₁, v₂, ...** を持つインスタンス **m::Mode[s₁⇒typeof(v₁), s₂⇒typeof(v₂), ...]** を構築します。いくつかまたはすべての **vᵢ** は省略されることがあり、その場合は `nothing` がデフォルトとなります。例: `Mode(:a => 25, :b, :c => "Hello world!")`。

```
Mode(s)
```

`nothing` 値を持つインスタンス **m::Mode[s⇒Nothing]** を構築します。型と値は、後続の呼び出し **m**`=>`**v** によって設定できます。複数のインスタンスは `~` 演算子で結合できます。例えば、`Mode(:a)=> 25 ~ Mode (:b) ~ Mode(:c)=> "Hello world!"` は `Mode(:a => 25, :b, :c =>  "Hello world!")` と同等です。

# インスタンスに対する操作

**m, m₁, m₂::Mode** とします。次のようになります。

  * `m => v` が与えられた場合 `m::Mode[s => Nothing]`: シンボル **s** が値と型の `v` を持つ新しいインスタンスを返します。
  * `m₁ ~ m₂`: `m₁` と `m₂` を結合します。同じシンボルを含む場合、ArgumentError をスローします。
  * `keys(m), values(m), pairs(m)`: シンボル / 値 / シンボルと値のペアを返します。
  * `m[s₁ [, s₂]... ]` （`sᵢ::Symbol` の場合）: `s₁` の値 / `s₁, s₂, ...` の値のタプルを返します。
  * `m[]`: `m` が1つの値のみを含む場合、それを返します。それ以外の場合は ArgumentError をスローします。
  * `checkmode(m, ...)`: `m` が `Mode` であり、指定されたシンボルを含むかどうかを確認し、必要に応じてアクションを実行します。詳細な説明については [`ArgumentModes.checkmode`](@ref) を参照してください。

# 例

### 1. 関数宣言と呼び出しでの使用

```julia-repl
julia> f(x) = println("Anything: $x")
       f(x::Mode[:iterator => Any]) = println("Values from iterator: $(x[]...)")
       f(x::Mode[:fromargs], y...) = println("Fromargs: $(y...)")
       function f(x::Union{Int, Mode[:a, :b, :c => Int]})
           checkmode(x, :a) do _;  println(":a")  end
           checkmode(x, :c) do c;  println(":c = $c")  end
           checkmode(x, :b) && println(":b")
           if x isa Int;  println("x = $x") end
       end
f (generic function with 4 methods)

julia> methods(f)
# 4 methods for generic function "f":
[1] f(x::Mode[:iterator => Any]) in Main at REPL[34]:1
[2] f(x::Mode[:fromargs], y...) in Main at REPL[36]:1
[3] f(x::Union{Int64, Mode[:c => Int64, :a, :b]}) in Main at REPL[38]:1
[4] f(x) in Main at REPL[33]:1

julia> f(25.0)
Anything: 25.0

julia> f(Mode(:iterator)=> 1:5)
Values from iterator: 12345

julia> f(Mode(:fromargs), 1, 2, 3, 4, 5)
Fromargs: 12345

julia> f(1)
x = 1

julia> f(Mode(:a, :c => 125))
:a
:c = 125

julia> f(Mode(:fromargs, :iterator => 1:5), 2)
ERROR: MethodError: no method matching f(::Mode[==, :iterator => UnitRange, :fromargs], ::Int64)
Closest candidates are:
  f(::Mode[:fromargs], ::Any...) at REPL[36]:1
  f(::Any) at REPL[33]:1
Stacktrace:
 [1] top-level scope
   @ REPL[59]:1

```

### 2. 型とインスタンスの構築、インスタンスに対する操作

```julia-repl
julia> M = Mode[:a => Real, :b => Union{Number, String}, :c]
Mode[:a => Real, :b => Union{Number, String}, :c]

julia> m1 = Mode(:a => 2.5, :c)
Mode[==, :a => Float64, :c]((a = 2.5, c = nothing))

julia> m1 isa M
true

julia> m2 = Mode(:a)=> 2.5 ~ Mode(:c)
Mode[==, :a => Float64, :c]((a = 2.5, c = nothing))

julia> m1 === m2
true

julia> Mode(:a => 2.5, :c, :d) isa M
false

julia> Mode(:a => "2", :c) isa M
false

julia> Mode(:a => 2.5, :c) ~ Mode(:b)=> "Hello world!"
Mode[==, :a => Float64, :c, :b => String]((a = 2.5, b = "Hello world!", c = nothing))

julia> Mode(:a => 2.5, :c) ~ Mode(:b)=> "Hello world!" ~ Mode(:a)=> 2
ERROR: ArgumentError: Duplicated keys :a

julia> checkmode(m, :a)
true

julia> checkmode(m, &, :a, :b, :g)
false

julia> checkmode(m, |, :a, :b, :g)
true

julia> m[:a, :c]
(2.5, nothing)

julia> m2 = Mode(:a => 2.5)
Mode[:a => Float64]((a = 2.5,))

julia> m2[]
2.5
```

# 注意

  * `show` は `Mode` の `DataType` に対して再定義され、型で宣言された **s⇒t** ペアのよりコンパクトで快適な提示が行われます。型の実際のシグネチャは `struct ArgnmentModes.Mode{NameType,  ValuesNamedTuple}` であり、`NameType` にはすべてのペア **s⇒t** が含まれ、`ValuesNamedTuple` にはシンボルに関連付けられた実際の値を格納するための `NamedTuple` が含まれます。
