```
XPRSgetcheckedmode()::checkedmode
```

この関数を使用して、現在のプロセスに対してすべての最適化関数呼び出しのチェックと検証が有効になっているかどうかを調査できます。

チェックと検証はデフォルトで有効ですが、XPRSsetcheckedmodeによって無効にすることができます。

# 戻り値

  * `checkedmode::Int32`: 現在のプロセスに対して最適化関数呼び出しのチェックと検証が無効になっている場合は0に設定され、それ以外の場合は非ゼロになります。

C APIの対応する関数[XPRSgetcheckedmode](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcheckedmode.html)のドキュメントも参照してください。
