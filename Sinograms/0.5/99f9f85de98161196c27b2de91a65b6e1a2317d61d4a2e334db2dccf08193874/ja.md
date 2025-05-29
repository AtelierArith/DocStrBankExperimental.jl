```
fbp(sino::AbstractMatrix ; kwargs...)
```

平行ビームシノグラムのサイズ `[nr × nϕ]` からのFBP再構成。サイズ `[nx × ny]` の画像を返します。

# オプション

  * `nx` : デフォルトは `nr`
  * `ny` : デフォルトは `nx`
  * `kwargs` : `fbp!` に渡される
