```
DockerManager(num_workers; kwargs...)
```

ローカルで実行されている [Docker](https://docs.docker.com/) デーモンサービスを介してワーカーを生成するクラスター管理者です。通常、単一のマシンでマルチマシンのJuliaコードをデバッグするために使用されます。

ローカルDockerクラスターを作成するには、Julia、DockerManagerを含むAWSClusterManagersのバージョン、およびdocker cliがすべてイメージに組み込まれた利用可能なDockerイメージが必要です。

次に、追加のDockerコンテナを生成できるDockerコンテナを作成できます：

docker run –network=host -v /var/run/docker.sock:/var/run/docker.sock –rm -it <image> julia

**注意**: コンテナが相互に通信できるようにするためには、ホストネットワーキングが必要です。DockerホストのUNIXソケットを転送する必要があるため、コンテナがホストのDockerプロセスと通信できるようになります。

## 引数

  * `num_workers::Int`: 生成するワーカーの数

## キーワード

  * `image::AbstractString`: 実行するdockerイメージ。
  * `timeout::Second`: ワーカーが利用可能になるまで待機する最大秒数。中止する前に。

## 例

```julia
julia> addprocs(DockerManager(4, "myproject:latest"))
```
