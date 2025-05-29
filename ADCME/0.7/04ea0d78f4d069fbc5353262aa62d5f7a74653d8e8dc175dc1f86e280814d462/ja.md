categorical(n::Union{PyObject, Integer}; kwargs...)

`kwargs` にはキーワード引数 `logits` があり、形状 `[batch_size, num_classes]` の 2-D テンソルです。各スライス `[i, :]` はすべてのクラスに対する非正規化対数確率を表します。
