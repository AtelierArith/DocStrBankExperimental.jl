このパッケージは、`LengthChannel{T} <: AbstractChannel{T}`という型を定義しており、これはイテレートされる際にチャネルの長さに関する情報を追加します。コンストラクタは`Channel`のコンストラクタと同様に動作しますが、長さを指定する追加の整数を受け取ります。この長さは、以下の例で`buf`と呼ばれるチャネルのバッファサイズと混同しないでください。`LengthChannel`がイテレートされると、指定された数の要素をイテレートするまで続き、その後はチャネルが閉じられます。たとえチャネルにさらに要素が追加されてもです。

例:

```julia
using LengthChannels, Test
len,buf = 10,4
lc = LengthChannel{Int}(len, buf) do ch
    for i = 1:100
        put!(ch, i)
    end
end

@test length(lc) == len
cc = collect(lc)
@test length(cc) == len
@test cc == 1:l
@test isopen(lc)
```

`LengthChannel`のコンストラクタは、指定された長さでイテレートした後にチャネルが自動的に閉じるかどうかを決定するキーワード引数`autoclose=false (default)`も受け取ります。指定された長さを何度もイテレートしたい場合は、チャネルを開いたままにしておくと便利です。ただし、チャネルがまだデータで満たされていることを確認してください。

## 機械学習のためのバッファ付きイテレータとしての使用

長さを持つチャネルの典型的な使用ケースは、機械学習モデルのトレーニング用のバッファ付きデータセットです。ここでは、ディスクからオーディオデータを読み込み、チャネルに入れる前に軽い前処理を行う例を示します。

```julia
using LengthChannels, Flux, Random
files      = readdir(path_to_datafiles)
buffersize = 10
dataset = LengthChannel{Vector{Float32}}(length(files), buffersize, spawn=true) do ch
    while true
        for file in shuffle(files)
            data = read_from_disk(file)
            put!(ch, data)
        end
    end
end
```

FluxでCNNモデルのトレーニングに適したバッチイテレータは、次のように取得できます。

```julia
batchsize  = 16
buffersize = 10
files      = readdir(path_to_datafiles)
dataset = LengthChannel{Array{Float32,4}}(length(files)÷batchsize, buffersize, spawn=true) do ch
    batch = Array{Float32,4}(undef,height,width,nchannels,batchsize)
    bi = 1
    while true
        for file in shuffle(files)
            data = read_from_disk(file)
            batch[:,:,:,bi] .= data
            bi += 1
            if bi > batchsize
                bi = 1
                put!(ch, copy(batch))
            end
        end
    end
end
```

ここで、`height,width,nchannels`はデータのサイズを指定する整数です。これで、`dataset`を`Flux.train!(loss, ps, dataset, opt)`に送信できます。
