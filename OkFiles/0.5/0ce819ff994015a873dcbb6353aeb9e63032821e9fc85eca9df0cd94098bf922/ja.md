`pathnorepeat(filepath; suffix_fun = serial_number_4d)` は、デフォルトで `serial_number_4d` を増加させることによって、重複しないファイルパスを返します。 `suffix_fun` は、`suffix_fun(n)` が整数 `n` によって更新された文字列を返す任意の関数として割り当てることができます。
