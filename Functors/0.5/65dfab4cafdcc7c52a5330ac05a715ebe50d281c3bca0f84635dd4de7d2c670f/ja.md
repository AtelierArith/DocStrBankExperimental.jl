```
KeyPath(keys...)
```

ネストされた構造内の値へのキーのパスを表すための型です。キーのシーケンスを使用して構築することも、他の `KeyPath` を連結することでも構築できます。キーは `Symbol`、`String`、`Int`、または `CartesianIndex` の型であることができます。

カスタム型の場合、シンボルキーによるアクセスは `getproperty` を使用して行われると想定されています。一貫性のために、メソッド `Base.propertynames` が有効なプロパティ名を取得するために使用されます。

文字列、整数、およびカートesianインデックスキーの場合、アクセスは `getindex` を使用して行われます。

参照: [`getkeypath`](@ref), [`haskeypath`](@ref).

# 例

```jldoctest
julia> kp = KeyPath(:b, 3)
KeyPath(:b, 3)

julia> KeyPath(:a, kp, :c, 4) # キーとキーパスを混ぜて構築
KeyPath(:a, :b, 3, :c, 4)

julia> struct T
           a
           b
       end

julia> function Base.getproperty(x::T, k::Symbol)
            if k in fieldnames(T)
                return getfield(x, k)
            elseif k === :ab
                return "ab"
            else        
                error()
            end
        end;

julia> Base.propertynames(::T) = (:a, :b, :ab);

julia> x = T(3, Dict(:c => 4, :d => 5));

julia> getkeypath(x, KeyPath(:ab)) # x.ab と同等
"ab"

julia> getkeypath(x, KeyPath(:b, :c)) # (x.b)[:c] と同等
4
```
