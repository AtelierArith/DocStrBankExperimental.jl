```
configure_optimisers(model, trainer)
```

`model`のために初期化されたオプティマイザの状態を返します。また、`scheduler`が現在のエポックを入力として受け取り、次のエポックの学習率として設定されるスカラーを返す任意の呼び出し可能オブジェクトであるタプル`(optimiser, scheduler)`を返すこともできます。

# 例

```julia
using Optimisers, ParameterSchedulers

function Tsunami.configure_optimisers(model::Model, trainer)
    return Optimisers.setup(AdamW(1f-3), model)
end

# 初期値1e-2から始まり、エポック[50, 100, 200]で学習率を10倍減少させるスケジューラを使用
function Tsunami.configure_optimisers(model::Model, trainer)

    function lr_scheduler(epoch)
        if epoch <= 50
            return 1e-2
        elseif epoch <= 100
            return 1e-3
        elseif epoch <= 200
            return 1e-4
        else
            return 1e-5
        end
    end
    
    opt_state = Optimisers.setup(AdamW(), model)
    return opt_state, lr_scheduler
end

# 上記と同じですが、ParameterSchedulersパッケージを使用しています。
function Tsunami.configure_optimisers(model::Model, trainer)
    lr_scheduler = ParameterSchedulers.Step(1f-2, 0.1f0, [50, 50, 100])
    opt_state = Optimisers.setup(AdamW(), model)
    return opt_state, lr_scheduler
end
```
