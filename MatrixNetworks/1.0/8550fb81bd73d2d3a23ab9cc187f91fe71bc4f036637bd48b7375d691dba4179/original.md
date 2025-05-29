# `havel_hakimi_graph`

Create a graph with a given degree sequence 

## Usage

`A = havel_hakimi_graph(d)` returns an instance of the  a graph with degree sequence d or throws ArgumentError if the degree sequence is not graphical.   

## Input

  * `d::Vector{Int}`:  a vector of integer valued degrees

## Output

-`A`: a matrix network for the undirected graph that results from the Havel-Hakimi procedure.
