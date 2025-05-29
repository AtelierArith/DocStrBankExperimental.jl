`NullNetworkLevel(data::DataFrame;num=100,fun="Null3",coinpvalue=0.5)`

Integration of some indicators of the bipartite network(original and null model).

# Argument

  * `data`:The adjacency matrix of a bipartite network.
  * `num`:Generated quantity of null model.
  * `fun`:Generation method of null model, you can select "Null1","Null2","Null3".
  * `coinpvalue`:Probability of true output(greater than 0 but less than 1).Please enter the value to one decimal place or two decimal places.

# Return

  * `df`:Integration of some indicators of the bipartite network(original and null model).

# Example

using BipartiteNull,DataFrames;

data=ExampleData(2);

print(data);

df=NullNetworkLevel(data)
