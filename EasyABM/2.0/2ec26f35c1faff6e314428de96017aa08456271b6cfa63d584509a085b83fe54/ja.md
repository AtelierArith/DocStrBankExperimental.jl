```julia
init_model!(
    model::EasyABM.GraphModel;
    initialiser,
    props_to_record
)

```

ユーザー定義の初期化関数を使用してシミュレーションを開始します。この関数はモデルを唯一の引数として受け取ります。エージェントおよびグラフのプロパティとともに、モデルのプロパティはユーザー定義の関数内で設定（または変更）でき、その後`init_model!`の`initialiser`引数として送信されます。時間の進化中に記録されるエージェント、ノード、エッジ、およびモデルのプロパティは、辞書引数`props_to_record`を通じて指定できます。記録されるエージェントプロパティのリストは、キー"agents"とプロパティ名のセットをシンボルとして値に指定することで設定されます。非空のエージェントプロパティのセットが指定されると、それは各エージェントの`keeps_record_of`プロパティを上書きします。ノード、エッジ、およびモデルのプロパティも同様に、キー"nodes"、"edges"、および"model"を使用して指定されます。
