```
TabularPolicy(V::Dict, Q::Dict, default)
TabularPolicy(default = NullPolicy())
```

状態値とアクションQ値がルックアップテーブル`V`と`Q`に格納されるポリシーソリューションで、`V`は状態ハッシュを値にマッピングし、`Q`は対応する状態の各アクションのQ値の辞書に状態ハッシュをマッピングします。

`default`ポリシーを指定することができ、ルックアップテーブルに状態が存在しない場合は、`default`によって返される値が代わりに使用されます。
