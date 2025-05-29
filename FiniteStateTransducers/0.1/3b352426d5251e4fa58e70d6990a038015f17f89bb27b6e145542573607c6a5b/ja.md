`arcmap(f::Function, fst::WFST, args...; modify_initials=identity, modify_finals=identity, isym=get_isym(fst), osym=get_osym(fst))`

`fst`から新しいWFSTを作成し、すべてのアークに関数`f`を適用します。`f`の引数は`args`で指定できます。

関数`modify_initials`と`modify_finals`は、初期および最終辞書で動作し、キーは初期/最終状態、値は対応する状態の重みです。

入力および出力テーブルも、キーワード`isym`および`osym`を使用して変更できます。

以下の例は、`arcmap`を使用してWFSTの重みのタイプを変換する方法を示しています：

```julia
julia> A = WFST(["a","b","c"]); # デフォルトでは重みはTropicalWeight{Float32}です

julia> add_arc!(A,1=>2,"a"=>"a",1);

julia> add_arc!(A,1=>3,"b"=>"c",3);

julia> initial!(A,1); final!(A,2,4); final!(A,3,2)
WFST #states: 3, #arcs: 2, #isym: 3, #osym: 3
|1/0.0f0|
a:a/3.0f0 → (2)
b:c/3.0f0 → (3)
((2/4.0f0))
((3/2.0f0))

julia> trop2prob(x) = ProbabilityWeight{Float64}(exp(-get(x)))
trop2prob (generic function with 1 method)

julia> function trop2prob(arc::Arc)
           ilab = get_ilabel(arc)
           olab = get_olabel(arc)
           w = trop2prob(get_weight(arc))
           n = get_nextstate(arc)
           return Arc(ilab,olab,w,n)
       end
trop2prob (generic function with 2 methods)

julia> trop2prob(initials::Dict) = Dict(i => trop2prob(w) for (i,w) in initials)
trop2prob (generic function with 3 methods)

julia> arcmap(trop2prob,A; modify_initials=trop2prob, modify_finals=trop2prob)
WFST #states: 3, #arcs: 2, #isym: 3, #osym: 3
|1/1.0|
a:a/0.3678794503211975 → (2)
b:c/0.049787066876888275 → (3)
((2/0.018315639346837997))
((3/0.1353352814912796))

```
