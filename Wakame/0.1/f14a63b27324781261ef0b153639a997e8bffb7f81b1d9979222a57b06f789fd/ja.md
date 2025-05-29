```
Mecab
```

MeCab タガーを表す可変構造体です。`Mecab()` コンストラクタを呼び出すことで作成されます。

# 例

```julia
tagger = Mecab()
results = parse(mecab, "すももももももももものうち")
```
