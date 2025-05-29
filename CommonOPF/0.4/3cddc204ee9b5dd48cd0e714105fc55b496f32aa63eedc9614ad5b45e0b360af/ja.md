```
split_at_busses(net::Network, at_busses::Vector{String}, with_busses::Vector{Vector{String}})
```

`p`を`at_busses`を各新しい`substation_bus`として分割し、対応する`with_busses`を含めます。`at_busses`と`with_busses`は`splitting_busses`を使用して決定できます。

注意：このバリエーションのsplt*at*bussesは、同じバスで2つ以上の分割を許可します。一方、split*at*bussesの他の実装は、分割バスの上と下のすべてのものを2つの部分に分割するだけです。
