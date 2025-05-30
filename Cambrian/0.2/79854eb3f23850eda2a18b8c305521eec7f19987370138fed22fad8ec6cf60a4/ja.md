すべての Individual サブタイプは次のメソッドを実装する必要があります: Individual(cfg::NamedTuple) Individual(json::String) mutate(ind::Individual) crossover(parents::Vararg{Individual})

およびフィールド genes fitness::Array を持つ必要があります。

BoolIndividual と FloatIndividual は Cambrian のデフォルトとして提供されています。
