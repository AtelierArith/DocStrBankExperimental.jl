```
activate(runnable, container_list)
```

コンテナをアクティブにします。これには、コンテナの起動と、実行可能なコードが実行された後のシャットダウンが含まれます。

ほとんどの場合、実行可能なコードは、エージェントシステムの目的を定義するためにシステム内でいくつかのプロセス（例えば、分散交渉など）を開始します。

一般的に、この関数は便利な関数であり、リスト内のすべてのコンテナを起動し、`runnable`によって表されるコードを実行し、再びコンテナをシャットダウンすることと同等です。さらに、この関数は、`runnable`を実行中に発生するエラーを処理し、コンテナがシャットダウンすることを保証します。

# 例

```julia
activate(your_containers) do 
   # システムを開始するための最初のメッセージを送信
   send_message(defined_agent, "Starting somethin", address(other_defined_agent))

   # しばらく待つ
   wait(some_stopping_condition)
end
```
