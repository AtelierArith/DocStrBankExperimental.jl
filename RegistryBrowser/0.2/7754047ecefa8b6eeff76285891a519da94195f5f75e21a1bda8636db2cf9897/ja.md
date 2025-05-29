```
registrybrowser(packagepattern=""; registrypattern="")
```

ターミナルでインタラクティブブラウザを起動し、Juliaセッションで利用可能なすべてのレジストリを閲覧し、これらのレジストリ内のすべてのパッケージに関する情報を取得できるようにします。

この関数を`packagepattern`を指定して呼び出すと、表示されるパッケージは`packagepattern`に一致する名前のパッケージに制限されます。同様に、`registrypattern`に一致する名前のレジストリのみが表示されます。`packagepattern`と`registrypattern`は、`AbstractString`または`Regex`型のいずれかであることができます。
