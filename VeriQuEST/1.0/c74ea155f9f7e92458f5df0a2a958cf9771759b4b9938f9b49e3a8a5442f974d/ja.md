```
throw_warning(::UntestedKrausFunction)
```

Kraus演算子がテストされていない場合に警告をスローします。具体的には、JuliaからCへのポインタインデックスを変換します。この関数がなくなるまで危険を冒して使用してください。

# 例

```julia
throw_warning(UntestedKrausFunction()) # "Kraus operator is not tested, specifically transalting a pointer index from Julia to C, use at peril till function goes away"というメッセージで警告をスローします
```
