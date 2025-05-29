```
run_with_logger(f::Function, logger::AbstractLogger, args...)
```

高度なイベントロギングを `f(args...)` の実行に適用するヘルパー関数です。

通常のログイベント（`@info` など）に加えて、ロガーは例外をキャッチしてエラーログイベントを作成します。その後、例外はキャッチされなかったかのように伝播を続けます。

### 入力

  * `f` – 実行する関数
  * `args` – 関数引数

### 戻り値

スローされた例外を含む `f(args...)` の適用結果。

### 注意事項

関数 `run_with_logger` は、関数呼び出し `f(args...)` に新しいロガーを適用します。「高いレベル」で適用されたすべてのロガーは、関数呼び出しの寿命の間置き換えられます。

### 例

```julia
logger = ConsoleLogger(stderr, Logging.Info)
run_with_logger(logger, -3) do number
    @info "負の数の平方根を計算: $number"
    sqrt(number)
end
```
