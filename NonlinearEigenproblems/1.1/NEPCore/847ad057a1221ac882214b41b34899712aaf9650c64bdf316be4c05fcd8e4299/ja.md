```
struct PrintLogger <: Logger ;
function PrintLogger(displaylevel)
```

このロガーを使用すると、stdoutに出力が得られ、他のログはありません。`displaylevel`パラメータは、どれだけ印刷されるべきかを指定します。値が高いほど、より多くの情報が印刷されます。ゼロは出力がないことを意味します。
