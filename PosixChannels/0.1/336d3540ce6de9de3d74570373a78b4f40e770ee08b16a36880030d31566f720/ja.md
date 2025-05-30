```
PosixChannel{T}(name, kwargs...)
```

`T`型のメッセージで動作する`PosixChannel`を作成します。

*注意*: `T`はプレーンデータ型でなければならず（`isbitstype`が`true`を返す必要があります）、メッセージキューは少なくとも`sizeof(T)`のメッセージを許可する必要があります。

# 拡張ヘルプ

# 引数

詳細については[`man 3 mq_open`](https://man7.org/linux/man-pages/man3/mq_open.3.html)を参照してください。

## すべての使用法

  * `mode::Symbol=:rw`: POSIXキューのオープニングモードで、`:r`、`:w`、または`:rw`のいずれかです。
  * `cloexec::Bool=false`: `O_CLOEXEC`フラグを有効にします。
  * `create::Bool=true`: `O_CREAT`フラグを有効にします。
  * `excl::Bool=false`: `O_CREAT`フラグを有効にします。
  * `nonblock::Bool=false`: `O_NONBLOCK`フラグを有効にします。

## 作成の詳細

新しいキューを作成する際（フラグ`O_CREAT`が有効な場合）、追加の情報を提供する必要があります。

  * `create_r_user::Bool=true`: ユーザーに対してキューを読み取り可能にします。
  * `create_w_user::Bool=true`: ユーザーに対してキューを書き込み可能にします。
  * `create_r_group::Bool=true`: ユーザーのグループに対してキューを読み取り可能にします。
  * `create_w_group::Bool=true`: ユーザーのグループに対してキューを書き込み可能にします。
  * `create_r_other::Bool=false`: 他のユーザーに対してキューを読み取り可能にします。
  * `create_w_other::Bool=false`: 他のユーザーに対してキューを書き込み可能にします。
  * `create_len::Int=systemmsgdefault()`: キュー内のメッセージの最大数。
  * `create_msg_size::Int=sizeof(T)`: メッセージの最大サイズ。

# 例

2つのjulia REPLを起動します（送信者と受信者）。

`sender.jl`:

```julia
using PosixChannels

chan = PosixChannel{Int}("posix_channels_are_fun", mode=:w)
print("データを送信する準備ができたら[Enter]を押してください。")
readline()

for i in 1:10
    put!(chan, i)
end

println("完了！")
println("チャネルを閉じています。")
close(chan)

```

`receiver.jl`

```julia
using PosixChannels

chan = PosixChannel{Int}("posix_channels_are_fun", mode=:r)
println("10個のIntの受信を待っています。送信を開始してください。")

for _ in 1:10
    while !isready(chan)
        wait(chan)
    end
    msg = take!(chan)
    println("受信したメッセージ: $msg")
end

println("完了！")
println("チャネルを閉じています。")
close(chan)
println("チャネルを削除しています。")
unlink(chan)
```

その後、各スクリプトを起動し、送信者のウィンドウでリターンを押すことができます。

```bash
$ julia --project sender.jl
データを送信する準備ができたら[Enter]を押してください。
完了！
チャネルを閉じています。
```

```bash
$ julia --project receiver.jl
10個のIntの受信を待っています。送信を開始してください。
受信したメッセージ: 1
受信したメッセージ: 2
受信したメッセージ: 3
受信したメッセージ: 4
受信したメッセージ: 5
受信したメッセージ: 6
受信したメッセージ: 7
受信したメッセージ: 8
受信したメッセージ: 9
受信したメッセージ: 10
完了！
チャネルを閉じています。
チャネルを削除しています。
```

!!! note "メッセージの種類"
    この例では整数を使用していますが、`isbitstype`を満たす任意の型を使用できます。例えば[`StaticStrings`](https://github.com/mkitti/StaticStrings.jl)を参照してください。


[`wait`](@ref)、[`put!`](@ref)、[`take!`](@ref)、[`unlink`](@ref)、[`isnonblocking`](@ref)も参照してください。
