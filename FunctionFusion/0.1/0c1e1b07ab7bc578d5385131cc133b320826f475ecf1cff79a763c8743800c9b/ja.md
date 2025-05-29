```
@switch_provider Name(Input)::Output = [Options...]
```

`Input`を`Output`に含まれる`Options`のどれにスイッチするかをマッピングするスイッチプロバイダーを作成します。`Output`が`AbstractVector`または`Tuple`の場合、`Input`は反復可能でなければならず、`Input`要素の数だけ構築されます。そうでない場合は、1つのアーティファクトのみが返されます。
