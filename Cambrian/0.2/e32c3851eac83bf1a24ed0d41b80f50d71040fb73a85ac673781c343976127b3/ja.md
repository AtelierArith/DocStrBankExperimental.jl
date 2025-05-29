すべてのAbstractEvolutionサブクラスは、次のフィールドを持つ必要があります：     config::NamedTuple     logger::CambrianLogger     population::Array{<:Individual} configについては、get*default*configを参照してください

進化クラスは次のメソッドを実装する必要があります：     populate(e::Evolution)     evaluate(e::Evolution)     generation(e::Evolution) デフォルト関数を参照してください。
