```
MovieLens(name; dir=nothing)
```

Datasets from the [MovieLens website](https://movielens.org) collected and maintained by [GroupLens](https://grouplens.org/datasets/movielens/).  The MovieLens datasets are presented in a Graph format.  For license and usage restrictions please refer to the Readme.md of the datasets.

There are 6 versions of MovieLens datasets currently supported: "100k",  "1m",  "10m", "20m", "25m", "latest-small".  The 100k and 1k datasets contain movie data and rating data along with demographic data. Starting from the 10m dataset, MovieLens datasets no longer contain the demographic data.  These datasets contain movie data, rating data, and tag information. 

The 20m and 25m datasets additionally contain [genome tag scores](http://files.grouplens.org/papers/tag_genome.pdf).  Each movie in these datasets contains tag relevance scores for every tag.

Each dataset contains an heterogeneous graph, with two kinds of nodes,  `movie` and `user`. The rating is represented by an edge between them: `(user, rating, movie)`.  20m, 25m, and latest-small datasets also contain `tag` nodes and edges of type `(user, tag, movie)` and  optionally `(movie, score, tag)`.

# Examples

## MovieLens 100K dataset

```julia-repl
julia> data = MovieLens("100k")
MovieLens 100k:
  metadata    =>    Dict{String, Any} with 2 entries
  graphs      =>    1-element Vector{MLDatasets.HeteroGraph}

julia> metadata = data.metadata
Dict{String, Any} with 2 entries:
  "genre_labels"      => ["Unknown", "Action", "Adventure", "Animation", "Children", "Comedy", "Crime", "Documentary", "Drama", "Fa…
  "movie_id_to_title" => Dict(1144=>"Quiet Room, The (1996)", 1175=>"Hugo Pool (1997)", 719=>"Canadian Bacon (1994)", 1546=>"Shadow…

julia> g = data[:]
  Heterogeneous Graph:
    node_types    =>    2-element Vector{String}
    edge_types    =>    1-element Vector{Tuple{String, String, String}}
    num_nodes     =>    Dict{String, Int64} with 2 entries
    num_edges     =>    Dict{Tuple{String, String, String}, Int64} with 1 entry
    edge_indices  =>    Dict{Tuple{String, String, String}, Tuple{Vector{Int64}, Vector{Int64}}} with 1 entry
    node_data     =>    Dict{String, Dict} with 2 entries
    edge_data     =>    Dict{Tuple{String, String, String}, Dict} with 1 entry

# Access the user information
julia> user_data = g.node_data["user"]
Dict{Symbol, AbstractVector} with 4 entries:
  :age        => [24, 53, 23, 24, 33, 42, 57, 36, 29, 53  …  61, 42, 24, 48, 38, 26, 32, 20, 48, 22]
  :occupation => ["technician", "other", "writer", "technician", "other", "executive", "administrator", "administrator", "student",…
  :zipcode    => ["85711", "94043", "32067", "43537", "15213", "98101", "91344", "05201", "01002", "90703"  …  "22902", "66221", "3…
  :gender     => Bool[1, 0, 1, 1, 0, 1, 1, 1, 1, 1  …  1, 1, 1, 1, 0, 0, 1, 1, 0, 1]

# Access rating information
julia> g.edge_data[("user", "rating", "movie")]
Dict{Symbol, Vector} with 2 entries:
  :timestamp => [881250949, 891717742, 878887116, 880606923, 886397596, 884182806, 881171488, 891628467, 886324817, 883603013  …  8…
  :rating    => Float16[3.0, 3.0, 1.0, 2.0, 1.0, 4.0, 2.0, 5.0, 3.0, 3.0  …  4.0, 4.0, 3.0, 2.0, 3.0, 3.0, 5.0, 1.0, 2.0, 3.0]
```

## MovieLens 20m dataset

```julia-repl
julia> data = MovieLens("20m")
MovieLens 20m:
  metadata    =>    Dict{String, Any} with 4 entries
  graphs      =>    1-element Vector{MLDatasets.HeteroGraph}

# There is only 1 graph in MovieLens dataset
julia> g = data[1]
Heterogeneous Graph:
  node_types    =>    3-element Vector{String}
  edge_types    =>    3-element Vector{Tuple{String, String, String}}
  num_nodes     =>    Dict{String, Int64} with 3 entries
  num_edges     =>    Dict{Tuple{String, String, String}, Int64} with 3 entries
  edge_indices  =>    Dict{Tuple{String, String, String}, Tuple{Vector{Int64}, Vector{Int64}}} with 3 entries
  node_data     =>    Dict{String, Dict} with 0 entries
  edge_data     =>    Dict{Tuple{String, String, String}, Dict} with 3 entries

# Apart from user rating a movie, a user assigns tag to movies and there are genome-scores for movie-tag pairs 
julia> g.edge_indices
  Dict{Tuple{String, String, String}, Tuple{Vector{Int64}, Vector{Int64}}} with 3 entries:
    ("movie", "score", "tag")   => ([1, 1, 1, 1, 1, 1, 1, 1, 1, 1  …  131170, 131170, 131170, 131170, 131170, 131170, 131170, 131170,…
    ("user", "tag", "movie")    => ([18, 65, 65, 65, 65, 65, 65, 65, 65, 65  …  3489, 7045, 7045, 7164, 7164, 55999, 55999, 55999, 55…
    ("user", "rating", "movie") => ([1, 1, 1, 1, 1, 1, 1, 1, 1, 1  …  60816, 61160, 65682, 66762, 68319, 68954, 69526, 69644, 70286, …

# Access the rating
julia> g.edge_data[("user", "rating", "movie")]
Dict{Symbol, Vector} with 2 entries:
  :timestamp => [1112486027, 1112484676, 1112484819, 1112484727, 1112484580, 1094785740, 1094785734, 1112485573, 1112484940, 111248…
  :rating    => Float16[3.5, 3.5, 3.5, 3.5, 3.5, 3.5, 4.0, 4.0, 4.0, 4.0  …  4.5, 4.0, 4.5, 4.5, 4.5, 4.5, 4.5, 3.0, 5.0, 2.5]

# Access the movie-tag scores
score = g.edge_data[("movie", "score", "tag")][:score]
23419536-element Vector{Float64}:
 0.025000000000000022
 0.025000000000000022
 0.057750000000000024
 ⋮
```

## References

[1] [GroupLens Website](https://grouplens.org/datasets/movielens/)

[2] [TensorFlow MovieLens Implementation](https://www.tensorflow.org/datasets/catalog/movielens)   

[3] Jesse Vig, Shilad Sen, and John Riedl. 2012. The Tag Genome: Encoding Community Knowledge to Support Novel Interaction. ACM Trans. Interact. Intell. Syst. 2, 3, Article 13 (September 2012), 44 pages. https://doi.org/10.1145/2362394.2362395.   

[4] F. Maxwell Harper and Joseph A. Konstan. 2015. The MovieLens Datasets: History and Context. ACM Trans. Interact. Intell. Syst. 5, 4, Article 19 (January 2016), 19 pages. https://doi.org/10.1145/2827872  
