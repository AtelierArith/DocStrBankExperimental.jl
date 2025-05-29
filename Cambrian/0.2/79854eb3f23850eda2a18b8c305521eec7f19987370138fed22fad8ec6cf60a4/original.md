every Individual subtype needs to implement: Individual(cfg::NamedTuple) Individual(json::String) mutate(ind::Individual) crossover(parents::Vararg{Individual})

and have the fields genes fitness::Array

BoolIndvidiual and FloatIndividual are provided as Cambrian defaults
