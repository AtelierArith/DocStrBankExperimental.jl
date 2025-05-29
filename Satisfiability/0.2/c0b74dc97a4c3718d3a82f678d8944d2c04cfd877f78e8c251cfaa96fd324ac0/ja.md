```
sat!(z::BoolExpr, solver=Z3())
sat!(z1, z2,..., solver=CVC5())
```

SAT問題をソルバーを使用して解決します。問題が充足可能な場合、`prob`内のすべての`BoolExprs`の値をその充足割り当てで更新します。

可能な返り値は`:SAT`、`:UNSAT`、または`:ERROR`です。`prob`は、返り値が`:SAT`の場合にのみブール値を追加するように変更されます。デフォルトでは、sat!は`prob`が充足不可能な場合、`prob`内の式の値を`nothing`にリセットします。この動作を変更するには、キーワード引数`clear_values_if_unsat`を使用します。例えば、`sat!(prob, solver=CVC5(), clear_values_if_unsat=false)`のようにします。

**代替使用法:**

```julia
    io = open("some_file.smt")
    status, values = sat!(io::IO, solver=CVC5())
    status, values = sat!(filename::String, solver=CVC5())
```

ioモードでは、sat!はJulia IOオブジェクトの内容を読み取り、それをソルバーに渡します。したがって、ユーザーは`read(io)`が完全かつ正しいSMT-LIBコマンドの文字列を返すことを確認する必要があります。これには`(check-sat)`または同等のものが含まれます。あるいは、`sat!`内で開いて閉じるファイル名を渡すこともできます。式は関数に渡されないため、`sat!`は充足割り当てを含む辞書を返します。

オプションのキーワード引数:

  * `solver::Solver`: 使用するソルバー。デフォルトは`Z3()`です。
  * `logic`: ソルバーの論理を手動で設定します。有効なSMT-LIB論理に対応する文字列でなければなりません。[valid SMT-LIB logic](http://smtlib.cs.uiowa.edu/logics.shtml)を参照してください。このオプションの設定方法が不明な場合は、設定しないでください - ほとんどのソルバーは自分で使用する論理を推測できます！
  * `line_ending::String`: 各SMT-LIBコマンドの後に使用する行末。Windowsではデフォルトで"\r\n"、それ以外の場所では"\n"です。
  * `clear_values_if_unsat=true`: trueの場合、式がunsatであれば、その値を`nothing`にリセットします。
  * `start_commands::String`: 式の前に含める追加のSMT-LIBコマンド、例えば`(set-logic LOGIC)`など。
  * `end_commands::String` : 式の後に含める追加のSMT-LIBコマンド。
