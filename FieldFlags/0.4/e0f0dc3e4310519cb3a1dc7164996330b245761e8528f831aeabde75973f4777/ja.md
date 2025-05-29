```
@bitflags [mutable] struct MyFlags
    flagA
    flagB
    _ # padding
    flagC
end
```

さまざまなブールフラグを表す構造体を構築します。各フラグは1ビットを占めるコンパクトな形式で保存されます。フィールドアクセスは`Bool`を返し、明示的なパディングはフィールド名を`_`とすることで宣言できます。パディング以外のフィールド名は一意である必要があります。この構造体はオプションで`mutable`としてマークできます。

詳細は[`@bitfield`](@ref)を参照してください。

!!! warning "構造体のサイズ"
    コンパイラの制限により、結果として得られるオブジェクトのサイズは（現在）常に8ビットの倍数になります。これにより追加されるビットはパディングと見なされ、存在することを信頼することはできません。将来のリリースで通知なしに削除される可能性があります。


# 例

```jldoctest
julia> @bitflags mutable struct MyFlags
           flagA
           flagB
           _ # padding
           flagC
       end

julia> flags = MyFlags(true, false, true)
MyFlags(flagA: true, flagB: false, flagC: true)

julia> flags.flagA
true

julia> flags.flagB
false

julia> flags.flagB = true
true

julia> flags.flagB
true

julia> sizeof(flags)
1
```
