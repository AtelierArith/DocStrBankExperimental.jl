```
make_card(list; word_size=12, line_width=8, break_words=false, kwargs...)
```

ビンゴカードを作成する

# 引数

  * `list`: ビンゴの単語を含む配列

# キーワード

  * `backend=pyplot`: プロットバックエンド。
  * `word_size`: 単語のサイズ（ポイント）
  * `line_width`: 各単語またはフレーズの行あたりの文字数
  * `break_words`: 単語を折り返す際に長い単語を分割する
  * `kwargs`: `plot`関数に渡す可変キーワード引数
