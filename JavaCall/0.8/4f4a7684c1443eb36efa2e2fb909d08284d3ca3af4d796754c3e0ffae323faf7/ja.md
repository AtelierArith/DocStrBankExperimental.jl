```
listmethods(obj::JavaObject, name::AbstractString)
```

渡されたjavaオブジェクトで利用可能なメソッドのリストを表示します。メソッドは渡された名前に基づいてフィルタリングされます。

### 引数

  * obj: javaオブジェクト
  * name: フィルター（例：メソッド名）

### 戻り値

javaオブジェクトで利用可能で、渡された名前に一致するメソッドのリスト
