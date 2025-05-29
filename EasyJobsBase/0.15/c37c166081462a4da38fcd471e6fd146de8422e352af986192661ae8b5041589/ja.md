```
Job(core::Thunk; description="", username="")
```

シンプルなジョブを作成します。

# 引数

  * `core`: ジョブコア定義を囲む `Thunk`。
  * `name`: ジョブに短い名前を付けます。
  * `description::String=""`: ジョブが何をするのかをより詳しく説明します。
  * `username::String=""`: ジョブを実行する人を示します。

# 例

```jldoctest
julia> using Thinkers

julia> a = Job(Thunk(sleep, 5); username="me", description="5秒間スリープします");

julia> b = Job(Thunk(run, `pwd` & `ls`); username="me", description="いくつかのコマンドを実行します");
```
