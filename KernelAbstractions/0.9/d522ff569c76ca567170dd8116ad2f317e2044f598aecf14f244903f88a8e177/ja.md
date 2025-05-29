```
@kernel config function f(args) end
```

これは2つの異なる設定を可能にします：

1. `cpu={true, false}`: CPU関数のコード生成を無効にします。これにより、KernelAbstractionsのプリミティブを非カーネル関数で使用できるようにセマンティクスが緩和されます。
2. `inbounds={false, true}`: ユーザーがすでにカーネル内で多くの`@inbounds`を使用している場合に、関数定義の周りに強制的に`@inbounds`マクロを有効にします。これは不正確な結果やクラッシュなどを引き起こす可能性があり、根本的に安全ではありません。注意してください！
3. `unsafe_indices={false, true}`: インデックスの暗黙の検証を無効にし、ユーザーは`@index(Global)`を避ける必要があります。

  * [`@context`](@ref)

!!! warn
    これは実験的な機能です。

