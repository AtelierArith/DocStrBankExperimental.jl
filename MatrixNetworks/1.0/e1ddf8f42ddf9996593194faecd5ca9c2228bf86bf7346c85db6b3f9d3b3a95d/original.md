# `is_graphical_sequence`

Check whether or not a degree sequence is graphical, which means that it is a valid degree sequence for  an undirected graph.

Note that this does not mean it is a valid degree sequence for a connected undirected graph. So, for instance,  `[1,1,1,1]`  is a valid degree sequence for two disconnected edges

## Usage

`is_graphical_sequence(d)` returns true or false 

## Input

  * `d::Vector{Int}`:  a vector of integer valued degrees

## Output

  * a boolean that is true if the sequence is graphical
