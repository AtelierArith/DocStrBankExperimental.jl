メソッドシグネチャ/プロトタイプ: `(n::Integer, ::Val{mask})::Nothing where {mask}`。

LLVMは、提供された整数`n`の最下位ビットが、符号なし値`mask`によってクリアされていると仮定します。後者は、`Val`を使用して型ドメインに渡されます。

!!! danger
    コンパイラに嘘をつくことは**危険**です。LLVMに誤った命題が真であると納得させることは、プログラムを微妙な方法で壊す可能性があります。

