散乱過程の文脈におけるすべての計算モデル定義の抽象基本型。`AbstractModelDefinition`のすべてのサブタイプは、基本的な相互作用に関連付けられています。したがって、次のソフトインターフェース関数を実装する必要があります。

```Julia
fundamental_interaction_type(::AbstractModelDefinition)
```
