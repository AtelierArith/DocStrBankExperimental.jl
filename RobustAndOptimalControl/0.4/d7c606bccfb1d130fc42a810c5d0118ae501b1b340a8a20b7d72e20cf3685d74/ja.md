```
ExtendedStateSpace{TE, T} <: AbstractStateSpace{TE}
```

二入力・二出力システムを表す型

```
z  ┌─────┐  w
◄──┤     │◄──
   │  P  │
◄──┤     │◄──
y  └─────┘  u
```

ここで

  * `z` は制御出力（パフォーマンス出力とも呼ばれる）を示します
  * `y` は測定出力を示します
  * `w` は外部入力（外乱や参照など）を示します
  * `u` は制御入力を示します

呼び出し `lft(P, K)` は（下部）線形分数変換を形成します 

```
z  ┌─────┐  w
◄──┤     │◄──
   │  P  │
┌──┤     │◄─┐
│y └─────┘ u│
│           │
│  ┌─────┐  │
│  │     │  │
└─►│  K  ├──┘
   │     │
   └─────┘
```

つまり、`K` の周りに下部ループを閉じます。

`ExtendedStateSpace` は `ss(P)` によって標準の `StateSpace` に変換できます。これにより、すべての入力と出力が保持され、実質的に分割が削除されます。

[`feedback`](@ref) がこの型に対して呼び出されると、フィードバックインデックスのデフォルトが自動的に設定されます。この型に対して定義されている他の関数には以下が含まれます

  * [`system_mapping`](@ref)
  * [`performance_mapping`](@ref)
  * [`noise_mapping`](@ref)
  * [`lft`](@ref)
  * [`feedback`](@ref) は `ExtendedStateSpace` のデフォルト接続を設定する特別なオーバーロードがあります。

次の設計関数は `ExtendedStateSpace` を入力として期待します

  * [`hinfsynthesize`](@ref)
  * [`h2synthesize`](@ref)
  * [`LQGProblem`](@ref) （他の型も受け入れます）

この型の使い方に関するビデオチュートリアルは [こちら](https://youtu.be/huYRrn--AKc) で入手できます。
