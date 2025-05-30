```julia
read_model_file(
    model_filepath::AbstractString;
    factor_eltype
) -> TensorInference.UAIModel

```

`model_filepath`で定義された問題インスタンスをUAIモデル形式で解析します。提供されたファイルパスが空の場合は、`nothing`を返します。

UAIファイル形式は次の場所で定義されています: https://uaicompetition.github.io/uci-2022/file-formats/
