query(ctx::PineconeContext, indexobj::PineconeIndex, queries::Vector{PineconeVector}, topk::Int64=10, namespace::String="", includevalues::Bool=false, includemeta::Bool=false, filter::Dict{String, Any}=Dict{String,Any}())

Query an index using the given context that match $queries$ passed in.  The $PineconeVector$ that is queries is a simple $PineconeVector$ as described above. Note there is an another version of $query()$ that takes in a $Vector{Vector{<:AbstractFloat}}$ for the $queries$ parameter.  Functionally equivalent. Returns JSON blob as a $String$ with the results on success, $nothing$ on failure.

topk is an optional parameter which defaults to 10 if not specified.  Do recommend using JSON3 to parse the blob.

# Example

```julia-repl
julia> testdict = Dict{String, Any}("genre"=>"documentary", "year"=>2019);
julia> pinecone_context = Pinecone.init("abcdef-1234-zyxv", "us-west1-gcp")
abcdef-1234-zyxv / us-west1-gcp / 1c9c2f3
julia> pinecone_index = Pinecone.Index("filter-example");
julia> testvector = Pinecone.PineconeVector("testid", [0.3,0.11,0.3,0.3,0.3,0.3,0.3,0.3,0.4,0.3], testdict)
PineconeVector is id: testid values: [0.3, 0.11, 0.3, 0.3, 0.3, 0.3, 0.3, 0.3, 0.4, 0.3]meta: Dict{String, Any}("genre" => "documentary", "year" => 2019)
julia> Pinecone.query(pinecone_context, pinecone_index, [testvector], 4)
"{"results":[{"matches":[{"id":"testid","score":3.98966023e-07,"values":[0.3,0.11,0.3,0.3,0.3,0.3,0.3,0.3,0.4,0.3]},{"id":"C","score":0.0461001098,"values":[0.3,0.3,0.3,0.3,0.3,0.3,0.3,0.3,0.3,0.3]}
],"namespace":""}]}"
```
