```
TypeUtils.@public args...
```

は `args...` を `public` として宣言しますが、エクスポートはされていません。Julia バージョン < 1.11 では、このマクロは何もしません。このマクロを使用することで、CI やカバレッジツールとのエラーを回避することもできます。
