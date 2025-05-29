```
@implement_gradient(f, f_dfdx)
```

このマクロは、関数 `f` の解析的導関数を提供する関数 `f_dfdx` を指定することを可能にし、`ForwardDiff.jl` に基づく自動微分を使用して `f` が微分されるときに呼び出されます（例えば、`Tensors.jl` の [`gradient`](@ref) または [`hessian`](@ref) を使用する場合、または `ForwardDiff.jl` の API のいずれかを使用する場合）。関数 `f_dfdx` は `f` と同じ引数を受け取り、`f` の値と勾配の両方を返す必要があります。すなわち、`fval, dfdx_val = f_dfdx(x)` です。以下の入力および出力タイプの組み合わせがサポートされています：

| `x`                 | `f(x)`              | `dfdx`              |
|:------------------- |:------------------- |:------------------- |
| `Number`            | `Number`            | `Number`            |
| `Number`            | `Vec`               | `Vec`               |
| `Number`            | `SecondOrderTensor` | `SecondOrderTensor` |
| `Vec`               | `Number`            | `Vec`               |
| `Vec`               | `Vec`               | `Tensor{2}`         |
| `SecondOrderTensor` | `Number`            | `SecondOrderTensor` |
| `SecondOrderTensor` | `SecondOrderTensor` | `FourthOrderTensor` |

注意すべきは、もし一つのテンソルが対称型であれば、すべてのテンソルが対称型でなければならないということです。
