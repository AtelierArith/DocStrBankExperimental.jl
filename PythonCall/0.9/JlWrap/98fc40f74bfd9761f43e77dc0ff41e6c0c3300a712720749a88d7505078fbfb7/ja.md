```
pyjlraw(v)
```

Juliaオブジェクト`x`をラップするPythonオブジェクトを作成します。

これは`juliacall.RawValue`型です。これは`pyjl(v)`よりもはるかに厳格な「Julian」インターフェースを持っています。たとえば、このオブジェクトの属性にアクセスしたり呼び出したりすると、常に`RawValue`が返されます。
