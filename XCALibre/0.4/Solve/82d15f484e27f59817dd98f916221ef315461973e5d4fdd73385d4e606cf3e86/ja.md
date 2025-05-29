```
set_runtime(; 
    # キーワード引数
    iterations::I, 
    write_interval::I, 
    time_step::N
    ) where {I<:Integer,N<:Number} = begin
    
    # 返される `NamedTuple`
        (
        iterations=iterations, 
        dt=time_step, 
        write_interval=write_interval)
end
```

これは、トップレベルのランタイム情報を設定するための便利な関数です。入力はすべてキーワード引数であり、シミュレーションを実行する直前にフローソルバーに基本情報を提供します。

# 入力引数

  * `iterations::Integer` は、シミュレーション実行の反復回数を指定します。
  * `write_interval::Integer` は、シミュレーション結果がファイルに書き込まれる頻度を定義します（現在の作業ディレクトリに）。この間隔は現在、反復回数に基づいています。結果をファイルに書き込まずに実行するには、`-1` に設定します。
  * `time_step::Number` は、シミュレーションで使用する時間ステップです。定常ソルバーの場合、これは単にカウンターであり、`1` を使用することをお勧めします。

# 例

```julia
runtime = set_runtime(
    iterations=2000, time_step=1, write_interval=2000)
```
