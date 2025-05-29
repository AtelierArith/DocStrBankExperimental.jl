```
is_initialized(m::T) where T <: ModelList
is_initialized(m::T, models...) where T <: ModelList
```

変数が初期化されているかどうかを確認し、初期化されていれば `true` を返し、そうでなければ `false` と情報メッセージを返します。

# 注記

ユーザーがシミュレーションするプロセスを事前に知る方法はないため、各プロセスにモデルを持つコンポーネントがある場合、初期化する必要がある変数は常にすべての中で最小のサブセットであり、他のモデルに必要な変数をユーザーがシミュレーションすると考えられます。

# 例

```@example
using PlantSimEngine

# パッケージ内の例として与えられたダミーモデルをロードします：
using PlantSimEngine.Examples

models = ModelList(
    process1=Process1Model(1.0),
    process2=Process2Model(),
    process3=Process3Model()
)

is_initialized(models)
```
