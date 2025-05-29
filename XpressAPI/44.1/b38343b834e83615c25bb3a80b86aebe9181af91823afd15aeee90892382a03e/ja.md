```
XPRSsetcheckedmode(checkedmode)::Nothing
```

この関数を使用して、Xpress Optimizer APIへの関数呼び出しおよび関数呼び出しパラメータのチェックと検証の一部を無効にすることができます。

このチェックは比較的軽量ですが、短時間に非集中的なXpress Optimizer関数が繰り返し呼び出される場合、無効にすることでパフォーマンスが向上する可能性があります。注意してください：関数呼び出しのチェックと検証を無効にした後、Xpress Optimizer関数の無効な使用が検出されず、Xpress Optimizerプロセスが予期しない動作をしたりクラッシュしたりする可能性があります。アプリケーション開発中に関数呼び出しのチェックと検証を無効にすることは推奨されません。

# 引数

  * `checkedmode::Integer`: 現在のプロセスからのすべてのXpress関数呼び出しの検証の多くを無効にするには、0を渡します。

C APIの対応する関数[XPRSsetcheckedmode](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetcheckedmode.html)のドキュメントも参照してください。
