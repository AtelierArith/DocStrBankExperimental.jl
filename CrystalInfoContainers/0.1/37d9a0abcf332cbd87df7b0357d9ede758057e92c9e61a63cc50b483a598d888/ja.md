get*assoc*index(t::TypedDataSource,name,index,other_name)

`t[other_name]`における`name[i]`に対応する値のインデックスを返します。`other_name`にリンクされたキー値がある場合、`name`が欠落している場合でもそれらがチェックされます。意図された使用法は、`other_name`がリンクされたキーのデータ名であることです。
