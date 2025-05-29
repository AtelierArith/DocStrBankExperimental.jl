```
@Job(job_description)
```

説明に基づいて新しいジョブを構築します。

## 説明フォーマット

```juila
MyNewJob = @Job begin
    # パラメータはジョブの入力値です 
    parameters = (param1::String, param2::Int, param)
    
    # 依存関係はこのジョブの入力として必要なジョブのリストです（オプション）
    # これらはパラメータを使用してプログラム的に作成でき、次のいずれかを返す必要があります
    # <:AbstractJob, AbstractArray{<:AbstractJob}, または AbstractDict{Symbol, <:AbstractJob}
    dependencies = [[SomeJob(i) for i in 1:param2]; AnotherJob("input")]
    
    # ターゲットは結果をキャッシュする出力場所です。ターゲットが存在する場合、ジョブは
    # スキップされ、キャッシュされた結果が返されます（オプション）。
    target = FileTarget(joinpath(snf_path, "raw_tables", "$month.csv"))
    
    # プロセス関数はジョブが呼び出されたときに実行されます。
    # すべてのパラメータ、`dependencies`、および `target` はこのスコープで定義されています。
    process = begin
        dep1_data = dependencies[1]
        x = do_logic(dep1_data, param1)
        write(target, x)
        return x
    end
end
```
