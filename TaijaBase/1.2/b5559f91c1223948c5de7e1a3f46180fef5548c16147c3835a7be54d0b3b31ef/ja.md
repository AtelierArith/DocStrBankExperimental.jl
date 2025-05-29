```
parallelize(
    parallelizer::nothing,
    f::Function,
    args...;
    kwargs...,
)
```

`AbstractParallelizer`が供給されていない場合は、単に関数を呼び出すか、ブロードキャストします。

## 開発者向けの注意

この関数は`TaijaBase`モジュールに属しており、`TaijaBase`に依存するパッケージに配布できるようにしていますが、`TaijaParallel`モジュールに依存する必要はありません。例えば、`CounterfactualExplanations`では、この関数を利用して反事実的説明の計算を並列化しています。ユーザーが明示的に並列化ツールを提供しない限り、この関数は単に関数`f`を呼び出すか、引数のコレクションに対してブロードキャストします。この単純な操作のために`TaijaParallel`に依存する必要はありません。
