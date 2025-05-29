```
get_compute_function(
    graph::DAG,
    instance,
    machine::Machine,
    context_module::Module
)
```

`compute_<id>(input::input_type(instance))` のシグネチャを持つ関数を返します。この関数は、与えられた入力に対するDAG計算の結果を返します。最終引数 `context_module` は常に `@__MODULE__` である必要があり、呼び出し元の環境で定義された関数を使用できるようにします。これを機能させるためには、トップレベルで次のようにする必要があります。

```Julia
using RuntimeGeneratedFunctions
RuntimeGeneratedFunctions.init(@__MODULE__)
```

## キーワード引数

`closures_size` (デフォルト=0 (オフ)): メイン生成コードで使用するクロージャのサイズ。これは、コンパイラが最適化できないコードブロックのサイズを指定します。十分に大きな関数の場合、大きな値はコンパイル時間が長くなるが、実行時間が速くなる可能性があります。**注意**: 実際に使用されるクロージャサイズは、ここで渡されたサイズとは異なる場合があります。関数は、与えられたサイズに基づいて、総ロケーション数のn乗根に近いサイズを自動的に選択します。`concrete_input_type` (デフォルト=`input_type(instance)`): 生成された関数の期待される入力タイプとして使用される型。省略した場合、問題インスタンスの `input_type` が使用されます。インスタンスの `input_type` は、生成された関数ヘッダーの注釈付き型としても使用されることに注意してください。
