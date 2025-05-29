```
@batchlens begin
    lens_expression_1
    lens_expression_2
    ...
    lens_expression_n
end
```

$$
n
$$

の "レンズ式" から $n$-タプルを取得/設定するレンズを作成します。各 "レンズ式" は `Setfield.@lens` によってサポートされる式であるか、他のレンズと `∘` を使って後合成された式です。

レンズの変換の重い作業をすべて行う [`batch`](@ref) も参照してください。

# 例

```jldoctest
julia> using Kaleido, Setfield

julia> lens = @batchlens begin
           _.a.b.c
           _.a.b.d ∘ converting(fromfield = x -> parse(Int, x), tofield = string)
           _.a.e
       end;

julia> obj = (a = (b = (c = 1, d = "2"), e = 3),);

julia> get(obj, lens)
(1, 2, 3)

julia> set(obj, lens, (10, 20, 30))
(a = (b = (c = 10, d = "20"), e = 30),)
```
