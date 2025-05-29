```
ss"substitution"
```

「静的」置換文字列は型ドメイン内にあります。基になる値は `unstatic()` 関数を使って抽出できます。

参照: `sr"regex"`, `nest`.

# 例

```julia
nt = (a_1=1, a_2=10, b_1=100)

# 正規表現と置換文字列で選択して名前を変更する:
nt[sr"a_(\d)" => ss"xxx_\1_xxx"] === (xxx_1_xxx = 1, xxx_2_xxx = 10)
```
