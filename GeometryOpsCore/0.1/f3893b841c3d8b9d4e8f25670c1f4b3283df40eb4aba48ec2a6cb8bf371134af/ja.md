```
WrongManifoldException{InputManifold, DesiredManifold, Algorithm} <: Exception
```

このエラーは、`Algorithm` が設計されていない多様体で呼び出されたときにスローされます。

主に `SingleManifoldAlgorithm` タイプを構築する際にスローされます。
