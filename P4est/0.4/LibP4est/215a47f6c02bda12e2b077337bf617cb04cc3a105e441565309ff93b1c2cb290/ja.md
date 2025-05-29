```
sc_abort_verbose(filename, lineno, msg)
```

標準エラー出力にメッセージを印刷し、その後 [`sc_abort`](@ref) () を呼び出します。

### プロトタイプ

```c
void sc_abort_verbose (const char *filename, int lineno, const char *msg) __attribute__ ((noreturn));
```
