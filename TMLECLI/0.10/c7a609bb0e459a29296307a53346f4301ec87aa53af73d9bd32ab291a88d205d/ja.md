```
RestrictedInteractionTransformer(;order=2, primary_variables=Symbol[], primary_variables_patterns=Regex[])
```

# 定義

このトランスフォーマーは、主変数のセットに基づいて相互作用項を生成します。生成されるすべての相互作用項は、主変数のセットと、提供されたテーブル内の残りの変数が最大1つで構成されます。主変数のセットを定義するのが (T₁, T₂) であり、テーブル内の残りの変数が (W₁, W₂) の場合、次数2の生成される相互作用項は次のようになります：

  * T₁xT₂
  * T₁xW₂
  * W₁xT₂

しかし、W₁xW₂は2つの残りの変数を含むため生成されません。

# 引数:

  * order: 指定された次数までのすべての相互作用特徴が計算されます
  * primary_variables: 相互作用を生成するための列名のセット
  * primary*variables*patterns: 主変数を特定するために追加で使用できる正規表現のセット
