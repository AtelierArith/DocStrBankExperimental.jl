```
make_colorscheme(dict;
    length=100,
    category="",
    notes="")
```

辞書の線分情報から新しいColorSchemeを作成します。`get_linear_segment_color(dict, n)`を0から1までのすべての`length`値に対して`n`として呼び出します。
