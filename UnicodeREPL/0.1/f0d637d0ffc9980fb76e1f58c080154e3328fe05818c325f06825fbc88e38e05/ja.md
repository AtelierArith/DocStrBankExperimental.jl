# UnicodeREPL

空行で、^を押すとunicode_replモードに入り、backspaceで退出します。

unicode_replモードでは、`\u(XXXX)`がタブ補完され、`XXXX`は任意の長さの16進数文字列であるUnicodeコードポイント`XXXX`のシンボルに補完されます。

## エクスポートされたシンボル

[`ufind`](@ref)
