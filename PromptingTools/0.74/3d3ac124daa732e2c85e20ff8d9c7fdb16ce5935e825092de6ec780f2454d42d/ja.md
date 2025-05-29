```
ConversationMemory
```

会話履歴を管理するための構造化されたコンテナです。`AbstractMessage`のベクターである唯一のフィールド`:conversation`を持っています。インテリジェントな切り捨てとキャッシングの動作（`get_last`）をサポートするように構築されています。

また、拡張された会話を持つためのファンクタとしても使用できます（`conversation`のkwargを常に渡すよりも簡単です）。

# 例

基本的な使用法

```julia
mem = ConversationMemory()
push!(mem, SystemMessage("あなたは役に立つアシスタントです"))
push!(mem, UserMessage("こんにちは！"))
push!(mem, AIMessage("こんにちは！"))

# または単に
mem = ConversationMemory(conv)
```

メモリ統計を確認

```julia
println(mem)  # ConversationMemory(2 messages) - システムメッセージはカウントしない
@show length(mem)  # 3 - すべてのメッセージをカウント
@show last_message(mem)  # 最後のメッセージを取得
@show last_output(mem)   # 最後のコンテンツを取得
```

異なるオプションで最近のメッセージを取得（システムメッセージ、ユーザーメッセージ、... + 最も最近のもの）

```julia
recent = get_last(mem, 5)  # 最後の5メッセージを取得（システムを含む）
recent = get_last(mem, 20, batch_size=10)  # キャッシングのために10のバッチに整列
recent = get_last(mem, 5, explain=true)    # 切り捨ての説明を追加
recent = get_last(mem, 5, verbose=true)    # 切り捨て情報を印刷
```

複数のメッセージを一度に追加（重複排除を行い、メモリを完全に保つ）

```julia
msgs = [
    UserMessage("元気ですか？"),
    AIMessage("私は元気です！"; run_id=1),
    UserMessage("素晴らしい！"),
    AIMessage("確かに！"; run_id=2)
]
append!(mem, msgs)  # run_idsなどに基づいて新しいメッセージのみを追加します。
```

AIとの会話に使用（会話を管理しやすくする）

```julia
response = mem("ジョークを教えて"; model="gpt4o")  # 自動的にコンテキストを管理
response = mem("もう一つ"; last=3, model="gpt4o")  # 最後の3メッセージのみを使用（`get_last`を使用）

# メモリからの直接生成
result = aigenerate(mem)  # 完全なコンテキストを使用して生成
```
