```
C_iio_context_get_version(context)
```

バックエンドのバージョンを取得します。

# パラメータ

  * `context::Ptr{iio_context}` : iio_context 構造体へのポインタ

# 戻り値

  * `ret::Int` : エラーがない場合は 0、そうでない場合は負のエラーコード
  * `major::Int` : メジャーバージョン
  * `minor::Int` : マイナーバージョン
  * `git_tag::String` : git タグ

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga342bf90d946e7ed3815372db22c4d3a6)
