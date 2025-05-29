```
values_as(varinfo[, Type])
```

`varinfo`内の値/実現を`Type`として返します。`Type`が実装されている場合。

`Type`が提供されていない場合、`varinfo`に保存されている値をそのまま返します。

# 例

`NamedTuple`を持つ`SimpleVarInfo`:

```jldoctest
julia> data = (x = 1.0, m = [2.0]);

julia> values_as(SimpleVarInfo(data))
(x = 1.0, m = [2.0])

julia> values_as(SimpleVarInfo(data), NamedTuple)
(x = 1.0, m = [2.0])

julia> values_as(SimpleVarInfo(data), OrderedDict)
OrderedDict{VarName{sym, typeof(identity)} where sym, Any} with 2 entries:
  x => 1.0
  m => [2.0]

julia> values_as(SimpleVarInfo(data), Vector)
2-element Vector{Float64}:
 1.0
 2.0
```

`OrderedDict`を持つ`SimpleVarInfo`:

```jldoctest
julia> data = OrderedDict{Any,Any}(@varname(x) => 1.0, @varname(m) => [2.0]);

julia> values_as(SimpleVarInfo(data))
OrderedDict{Any, Any} with 2 entries:
  x => 1.0
  m => [2.0]

julia> values_as(SimpleVarInfo(data), NamedTuple)
(x = 1.0, m = [2.0])

julia> values_as(SimpleVarInfo(data), OrderedDict)
OrderedDict{Any, Any} with 2 entries:
  x => 1.0
  m => [2.0]

julia> values_as(SimpleVarInfo(data), Vector)
2-element Vector{Float64}:
 1.0
 2.0
```

`Metadata`の`NamedTuple`を持つ`VarInfo`:

```jldoctest
julia> # 面倒なので、例のモデルを使って`VarInfo`を構築します。
       vi = DynamicPPL.typed_varinfo(DynamicPPL.TestUtils.demo_assume_dot_observe());

julia> vi[@varname(s)] = 1.0; vi[@varname(m)] = 2.0;

julia> # 簡潔さのために、型だけを確認します。
       md = values_as(vi); md.s isa Union{DynamicPPL.Metadata, DynamicPPL.VarNamedVector}
true

julia> values_as(vi, NamedTuple)
(s = 1.0, m = 2.0)

julia> values_as(vi, OrderedDict)
OrderedDict{VarName{sym, typeof(identity)} where sym, Float64} with 2 entries:
  s => 1.0
  m => 2.0

julia> values_as(vi, Vector)
2-element Vector{Float64}:
 1.0
 2.0
```

`Metadata`を持つ`VarInfo`:

```jldoctest
julia> # 面倒なので、例のモデルを使って`VarInfo`を構築します。
       vi = DynamicPPL.untyped_varinfo(DynamicPPL.TestUtils.demo_assume_dot_observe());

julia> vi[@varname(s)] = 1.0; vi[@varname(m)] = 2.0;

julia> # 簡潔さのために、型だけを確認します。
       values_as(vi) isa Union{DynamicPPL.Metadata, Vector}
true

julia> values_as(vi, NamedTuple)
(s = 1.0, m = 2.0)

julia> values_as(vi, OrderedDict)
OrderedDict{VarName{sym, typeof(identity)} where sym, Float64} with 2 entries:
  s => 1.0
  m => 2.0

julia> values_as(vi, Vector)
2-element Vector{Real}:
 1.0
 2.0
```
