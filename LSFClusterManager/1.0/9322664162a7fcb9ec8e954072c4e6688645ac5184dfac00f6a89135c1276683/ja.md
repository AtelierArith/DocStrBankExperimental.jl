```
addprocs_lsf(np::Integer;
             bsub_flags::Cmd=``,
             bpeek_flags::Cmd=`-f`,
             ssh_cmd::Cmd=``,
             bsub_cmd::Cmd=`bsub`,
             bpeek_cmd::Cmd=`bpeek`,
             retry_delays=ExponentialBackOff(n=10,
                                             first_delay=1, max_delay=512,
                                             factor=2),
             throttle::Integer=np,
             params...) =
```

IBMのプラットフォーム負荷分散施設によって管理されているクラスターで`np`ワーカーを起動します。 `bsub_flags`は、クラスターまたはワークフローのニーズに特有のフラグを`bsub`に渡すために使用できます。 `ssh_cmd`は、クラスターのヘッドノード以外からワーカーを起動するために使用できます（例：個人のワークステーション）。 `retry_delays`は、ワーカーが起動するのを繰り返し待つ時間を秒単位で指定する数のベクトルです。 `throttle`は、一度に起動するワーカーの数を指定します。 bpeekフラグに`-f`を含める（デフォルト）と、ワーカーのstdoutがマスターにも表示されます。

# 例

```
addprocs_lsf(1000; ssh_cmd=`ssh login`, throttle=10)
```
