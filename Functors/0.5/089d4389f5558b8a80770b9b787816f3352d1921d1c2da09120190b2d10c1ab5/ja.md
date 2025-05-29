```
fmap(f, x, ys...; exclude = Functors.isleaf, walk = Functors.DefaultWalk(), [prune])
```

構造体と型を保持する `map`。

デフォルトでは、`f` を適用することによって `exclude`（デフォルトは [`isleaf`](@ref Functors.isleaf)）で特定されるすべてのリーフノードを変換し、それ以外の場合は [`functor`](@ref Functors.functor) を使用して `x` を再帰的にトラバースします。オプションで、同じツリー構造を持つオブジェクト `ys` にも関連付けることができます。その場合、`f` は `x` と `ys` の対応するリーフノードに適用されます。

[`fmap_with_path`](@ref) および [`fmapstructure`](@ref) も参照してください。

# 例

```jldoctest
julia> fmap(string, (x=1, y=(2, 3)))
(x = "1", y = ("2", "3"))

julia> nt = (a = [1,2], b = [23, (45,), (x=6//7, y=())], c = [8,9]);

julia> fmap(println, nt)
[1, 2]
23
45
6//7
()
[8, 9]
(a = nothing, b = Any[nothing, (nothing,), (x = nothing, y = nothing)], c = nothing)

julia> fmap(println, nt; exclude = x -> x isa Array)
[1, 2]
Any[23, (45,), (x = 6//7, y = ())]
[8, 9]
(a = nothing, b = nothing, c = nothing)

julia> twice = [1, 2];  # println はこれに対して一度だけ作用する

julia> fmap(println, (i = twice, ii = 34, iii = [5, 6], iv = (twice, 34), v = 34.0))
[1, 2]
34
[5, 6]
34
34.0
(i = nothing, ii = nothing, iii = nothing, iv = (nothing, nothing), v = nothing)

julia> d1 = Dict("x" => [1,2], "y" => 3);

julia> d2 = Dict("x" => [4,5], "y" => 6, "z" => "an_extra_value");

julia> fmap(+, d1, d2) == Dict("x" => [5, 7], "y" => 9) # "z" は無視されることに注意
true
```

複数回出現する可変オブジェクトは、`IdDict` に `f(x)` をキャッシュすることによって一度だけ処理されます。したがって、関係 `x.i === x.iv[1]` は保持されます。二回出現する不変オブジェクトはキャッシュに保存されないため、`f(34)` は二回呼び出され、結果は `f` が純粋である場合にのみ一致します。

デフォルトでは、ほとんどすべてのコンテナのような型には再帰する子供がいます。数の配列にはありません。

カスタム型の再帰をオプトアウトするには、[`@leaf`](@ref) を使用するか、カスタム `exclude` 関数を渡します。

```jldoctest withfoo
julia> struct Foo; x; y; end

julia> struct Bar; x; end

julia> m = Foo(Bar([1,2,3]), (4, 5, Bar(Foo(6, 7))));

julia> fmap(x -> 10x, m)
Foo(Bar([10, 20, 30]), (40, 50, Bar(Foo(60, 70))))

julia> fmap(string, m)
Foo(Bar("[1, 2, 3]"), ("4", "5", Bar(Foo("6", "7"))))

julia> fmap(string, m, exclude = v -> v isa Bar)
Foo("Bar([1, 2, 3])", (4, 5, "Bar(Foo(6, 7))"))
```

再構築せずにカスタム型に再帰するには、[`fmapstructure`](@ref) を使用します。

トラバースの動作を高度にカスタマイズするには、[`Functors.AbstractWalk`](@ref) をサブタイプ化したカスタム `walk` 関数を渡します。呼び出し `fmap(f, x, ys...; walk = mywalk)` は、[`ExcludeWalk`](@ref) の中に `mywalk` をラップし、その後 [`CachedWalk`](@ref) になります。ここで、[`ExcludeWalk`](@ref) は除外されたノードで `f` を適用する責任があります。ユーザーが構築したウォークを実行するための低レベルインターフェースについては、[`execute`](@ref) を参照してください。

```jldoctest withfoo
julia> struct MyWalk <: Functors.AbstractWalk end

julia> (::MyWalk)(recurse, x) = x isa Bar ? "hello" :
                                            Functors.DefaultWalk()(recurse, x)

julia> fmap(x -> 10x, m; walk = MyWalk())
Foo("hello", (40, 50, "hello"))
```

同じノードが二回出現する場合の動作は、`prune` キーワードに値を与えることによって変更でき、その値は最初以外のすべての場所で使用されます：

```jldoctest
julia> twice = [1, 2];

julia> fmap(float, (x = twice, y = [1,2], z = twice); prune = missing)
(x = [1.0, 2.0], y = [1.0, 2.0], z = missing)
```
