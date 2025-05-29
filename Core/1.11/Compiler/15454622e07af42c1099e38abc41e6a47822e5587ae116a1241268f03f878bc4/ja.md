```
alias::MustAlias
```

この格子要素は、親オブジェクトのアイデンティティを記録しながらオブジェクトフィールドへの参照をラップします。これは、`isa`や`===`のような組み込み関数によってオブジェクトフィールドタイプに課せられる特定の制約が、同じオブジェクトフィールドへの別の参照に伝播されることを可能にします。重要な点は、この格子要素がラップされたスロットオブジェクトのフィールドがスロットオブジェクトが再割り当てされるまで決して変わらないという不変条件を仮定していることです。これは、ラップされたオブジェクトフィールドが定数であるべきであることを意味します。現在、推論はオブジェクトごとのメモリ効果を追跡しないためです。特に、`maybe_const_fldidx`は、与えられた格子要素が`MustAlias`によってラップされる資格があるかどうかを確認するためにリフトを取ります。例：

```juila
let alias = getfield(x::Some{Union{Nothing,String}}, :value)::MustAlias(x, Some{Union{Nothing,String}}, 1, Union{Nothing,String})
    if alias === nothing
        # 現在`getfield(x, :value)`が`nothing`であると仮定できます
    else
        # 現在`getfield(x, :value)`が`::String`であると仮定できます
    end
end
```

N.B. 現在、この格子要素はabstractinterpretでのみ使用されており、最適化では使用されていません。
