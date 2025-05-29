```
get_ICD_code_range(range::String)
```

`revision`の`range[1]`と`range[2]`の間にあるすべてのコードを取得します。

# パラメータ

  * `range::String`: `code_1-code_2`の形式の`String`でなければならず、code*1とcode*2は2つのコード（その改訂は`revision`によって指定されます）です；
  * `revision::String`: `"ICD-9"`または`"ICD-10"`のいずれかでなければなりません。
