```
Resnet1D(out_features::Int64, hidden_features::Int64;
    num_blocks::Int64=2, activation::Union{String, Function, Nothing} = "relu", 
    dropout_probability::Float64 = 0.0, use_batch_norm::Bool = false, name::Union{String, Missing} = missing)
```

1D残差ネットワークを作成します。`name`がmissingでない場合、`Resnet1D`は新しいエンティティを作成しません。

# 例

```julia
resnet = Resnet1D(20)
x = rand(1000,10)
y = resnet(x)
```

# 例: 数字認識

```
using MLDatasets
using ADCME

# データをロード 
train_x, train_y = MNIST.traindata()
train_x = reshape(Float64.(train_x), :, size(train_x,3))'|>Array
test_x, test_y = MNIST.testdata()
test_x = reshape(Float64.(test_x), :, size(test_x,3))'|>Array

# 損失関数を構築 
ADCME.options.training.training = placeholder(true)
x = placeholder(rand(64, 784))
l = placeholder(rand(Int64, 64))
resnet = Resnet1D(10, num_blocks=10)
y = resnet(x)
loss = mean(sparse_softmax_cross_entropy_with_logits(labels=l, logits=y))

# ニューラルネットワークを訓練 
opt = AdamOptimizer().minimize(loss)
sess = Session(); init(sess)
for i = 1:10000
    idx = rand(1:60000, 64)
    _, loss_ = run(sess, [opt, loss], feed_dict=Dict(l=>train_y[idx], x=>train_x[idx,:]))
    @info i, loss_
end

# テスト 
for i = 1:10
    idx = rand(1:10000,100)
    y0 = resnet(test_x[idx,:])
    y0 = run(sess, y0, ADCME.options.training.training=>false)
    pred = [x[2]-1 for x in argmax(y0, dims=2)]
    @info "Accuracy = ", sum(pred .== test_y[idx])/100
end
```

![](https://github.com/ADCMEMarket/ADCMEImages/tree/master/ADCME/assets/resnet.png?raw=true)
