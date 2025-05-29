```
@specset [option option=val ...] default_args... begin ... end
@specset [option option=val ...] default_args... for v in (...) ... end
@specset [option option=val ...] default_args... for v in (...), w in (...) ... end
```

共有のデフォルト値を持つ[`StatsSpec`](@ref)のベクターを構築し、その後[`proceed`](@ref)を呼び出して手続きを実行します。[`StatsSpec`](@ref)のベクターと結果オブジェクトのベクターが返されますが、`option`で指定された代替の動作がある場合はそれに従います。

# 引数

  * `[option option=val ...]`: [`proceed`](@ref)のキーワード引数を含む`@specset`のオプション設定。
  * `default_args...`: すべての[`StatsSpec`](@ref)で共有される引数のオプションデフォルト値。
  * `code block`: [`StatsSpec`](@ref)を構築するための引数を含む`begin/end`ブロックまたは`for`ループ。

# 注意事項

`@specset`は、[`StatsSpec`](@ref)を構築する`Expr`を変換し、コードブロックから引数のセットを収集し、[`StatsSpec`](@ref)内で呼び出される関数の名前に基づいてユーザーが入力した引数をどのように処理する必要があるかを推測します。エンドユーザー向けには、これらの関数呼び出しのための`Expr`を生成する`Macro`が提供されるべきです。

オプションのデフォルト引数は、各個別の仕様に提供された引数とマージされ、[`default`](@ref)を介して各[`StatsStep`](@ref)に関連付けられたデフォルト値を上書きします。これらのデフォルト引数は、コードブロック内の各仕様に対して引数が指定される方法と同じパターンで指定する必要があります。`@specset`は、コードブロック内で見つかった同じ関数を呼び出すことによってこれらの引数を処理します。

`@specset`の動作に関するオプションは、最初の引数としてブラケット`[...]`内に提供でき、各オプションは空白で区切られます。ブール値を取るオプションについては、オプションの名前を指定するだけで値をtrueに設定できます。

`@specset`の動作を変更するための以下のオプションが利用可能です：

  * `noproceed::Bool=false`: [`proceed`](@ref)を呼び出さず、[`StatsSpec`](@ref)のベクターのみを返します。
  * `verbose::Union{Bool,IO}=false`: 各ステップの名前を呼び出されたときに`stdout`または指定された`IO`ストリームに印刷します。
  * `keep=nothing`: 返される追加オブジェクトの名前（`Symbol`型）。
  * `keepall::Bool=false`: [`StatsSpec`](@ref)からの引数とともに手続きによって生成されたすべてのオブジェクトを返します。
  * `pause::Int=0`: 指定されたステップ数を完了した後に[`StatsStep`](@ref)の反復を中断します（デバッグ用）。
