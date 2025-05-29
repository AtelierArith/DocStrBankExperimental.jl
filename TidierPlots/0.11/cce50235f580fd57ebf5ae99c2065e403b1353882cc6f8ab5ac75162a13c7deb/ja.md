```
label_wrap(width)
```

指定された幅にテキスト文字列をラップし、スペースで折り返します。

# 引数

  * `width`: ラップする前の行の最大文字数。

# 例

```julia
labeler = label_wrap(10)
labeler(["This is a long sentence."]) # ["This is a
long
sentence."]
```
