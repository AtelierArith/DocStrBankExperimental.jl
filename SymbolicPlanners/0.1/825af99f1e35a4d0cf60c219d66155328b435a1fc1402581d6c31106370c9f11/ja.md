```
TabularVPolicy(V::Dict, domain, spec, default)
TabularVPolicy(domain, spec, default = NullPolicy())
```

状態値が状態ハッシュを値にマッピングするルックアップテーブル `V` に保存されるポリシーソリューション。ポリシーが各状態でアクションQ値を導出する方法を知るために、ドメインと仕様も提供する必要があります。

`default` ポリシーを指定することができるので、状態がルックアップテーブルにまだ存在しない場合、`default` によって返される値が代わりに使用されます。
