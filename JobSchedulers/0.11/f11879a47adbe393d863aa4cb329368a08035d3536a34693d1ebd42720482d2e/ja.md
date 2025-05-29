```
@submit [option=value]... expr
```

`expr`からジョブを提出します。`expr`に`Job`が**明示的に**表示されている場合、`DONE => job`が依存関係リストに自動的に追加されます。

  * `expr`: 任意のタイプの`Expr`がサポートされています。
  * `option = value`: [`Job`](@ref)のキーワード引数。`expr`が`Pipelines.Program`として解析される場合、`option`にはその入力、出力、および実行キーワード引数も含まれます。

[`Job`](@ref)、[`submit!`](@ref)も参照してください。

## 例

```julia
j = @submit 1+1
wait(j)
@assert result(j) == 2

# `Job`がサポートする任意のキーワード引数を使用できます。例えば`name`、`ncpu`など：
j_2sec = @submit name = "2秒後に実行" begin sleep(2); 32 end

# `j_2sec isa Job`であるため、`DONE => j_2sec`が`j2.dependency`にプッシュされます。
j2 = @submit mem=2KB begin
    1 + result(j_2sec)
end

wait(j2)
@assert result(j2) == 1 + 32

# `expr`に含まれていない依存関係を手動で追加することもできます：
j3 = @submit dependency = [PAST => j] println("j3が完了しました。j2の結果 = ", result(j2))

# 注意: j3.dependencyは提出後に空になる可能性があります。なぜなら、JobSchedulerは依存関係リスト内で状態に達したジョブを削除するからです。
```

!!! warning "明示的なジョブのみが自動的に依存関係に追加されます"
    `@submit`はコンテナ内の要素を知ることができないため、コンテナ内のジョブ依存関係を追加するために歩き回ることができません。

    ```julia
    jobs = Job[]  # ジョブコンテナ
    for i in 1:2
        push!(jobs, @submit begin sleep(30);i end) # 10個のジョブが`jobs`に追加されます
    end

    x = 0
    j_something_wrong = @submit for j in jobs
        # グローバルxを使用する必要があります
        global x += result(j)
    end
    # ┌ Warning: 実行中のジョブから結果を取得しています: 戻り値は予期しないものになる可能性があります。
    # └ @ JobSchedulers ~/projects/JobSchedulers.jl/src/jobs.jl:318

    result(j_something_wrong)
    # MethodError(+, (nothing, nothing), 0x0000000000007b16)
    ```

    これを避けるために、(1) `submit!`を使用するか、(2) `@submit`に`dependency = jobs`を明示的に追加します。

    ```julia
    x = 0
    j_ok = submit!(dependency = jobs) do
        for j in jobs
            # グローバルxを使用する必要があります
            global x += result(j)
        end
    end
    wait(j_ok)
    @assert x == 55

    x = 100
    j_ok_too = @submit dependency = jobs for j in jobs
        # グローバルxを使用する必要があります
        global x += result(j)
    end
    wait(j_ok_too)
    @assert x == 155
    ```

