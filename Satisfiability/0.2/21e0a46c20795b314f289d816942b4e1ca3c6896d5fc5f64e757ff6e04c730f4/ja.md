```
interactive_solver = open(Z3()) # インタラクティブソルバーのプロセスを開く
status, values = sat!(interactive_solver, exprs...) # exprsの充足可能性をチェックする
```

インタラクティブソルバーのプロセスで作業する際は、`(check-sat)`コマンドを発行します。オプションの`exprs`は、`(check-sat)`が発行されるときに仮定されますが、スタックには**主張されません**。これは、SMT-LIBの`(check-sat-assuming expr1, expr2,...)`コマンドと同等です。

主張が行われていない場合、`sat!`はエラーをスローします。

**このモードでは、`sat!`は関数呼び出しで提供された`exprs`の値のみを設定できます** つまり、`assert(expr1)`を行い、その後に`sat!(interactive_solver, expr2)`を呼び出すと、`value(expr1)`は`nothing`になります **問題がSATであっても**。これを緩和するために、`sat!`は`(status, values)`を返し、`values`は変数名と充足する割り当てのDictです。`expr1`の値を割り当てるには、`assign!(values, expr1)`を呼び出します。

オプションのキーワード引数：

  * `logic`: ソルバーのロジックを手動で設定します。これは[有効なSMT-LIBロジック](http://smtlib.cs.uiowa.edu/logics.shtml)に対応する文字列でなければなりません。このオプションの設定方法が不明な場合は、設定しないでください - ほとんどのソルバーは自分で使用するロジックを推測できます！
  * `line_ending::String`: 各SMT-LIBコマンドの後に使用する行末。Windowsではデフォルトで"\r\n"、それ以外の場所では"\n"です。
