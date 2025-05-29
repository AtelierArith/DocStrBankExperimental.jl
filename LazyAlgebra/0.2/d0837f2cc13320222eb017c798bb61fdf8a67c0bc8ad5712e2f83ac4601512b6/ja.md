```
input_type([P=Direct,] A)
output_type([P=Direct,] A)
```

は、マッピング `A` を持つ操作 `P` の入力および出力引数の（推奨）型を返します。 `A` がJulia配列に対して操作を行う場合、入力および出力の要素型、次元のリスト、`i`-次元および次元数は次のように与えられます：

```
input_eltype([P=Direct,] A)          output_eltype([P=Direct,] A)
input_size([P=Direct,] A)            output_size([P=Direct,] A)
input_size([P=Direct,] A, i)         output_size([P=Direct,] A, i)
input_ndims([P=Direct,] A)           output_ndims([P=Direct,] A)
```

Julia配列に対して操作を行うマッピングの場合、`input_size(A)` と `output_size(A)` のみを実装する必要があります。

また、次も参照してください: [`vcreate`](@ref), [`apply!`](@ref), [`LinearMapping`](@ref), [`Operations`](@ref).
