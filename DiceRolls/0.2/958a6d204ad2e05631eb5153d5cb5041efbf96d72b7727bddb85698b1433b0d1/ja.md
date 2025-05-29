```
@roll_str(str)
```

便利な文字列マクロ。フォーマット: <n rolls>#<N>d<faces>+<modifier><mod effect>

<n rolls>、<N>、<modifier>、<mod effect>はオプションです。

例:

```
r"2#1d20+6" # 1d20+6を2回振る
r"2d20kh1" # 2d20を振って最高値を保持する
```
