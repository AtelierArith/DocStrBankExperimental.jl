```
PrefectBlock <: AbstractPrefectBlock
```

Constructors:

```
PrefectBlock(blockname::String)
PrefectBlock(blockname::String, api::PrefectAPI)
PrefectBlock(blockname::String, block::AbstractPrefectBlock)
```

Returns a Prefect Block from the Prefect server, the block data is stored in the `block` field. Prefect Block names are strings called 'slugs', formatted as `block-type-name/block-name`. A Prefect Block is uniquely specified by its name and the Prefect DB where it is stored, therefore the API URL is necessary for the constructor. The single-argument constructor takes the default PrefectAPI() as the Prefect Server endpoint.

A non-server block can be constructed by supplying an AbstractPrefectBlock object.

The AbstractPrefectBlock types are meant to mirror the functionality defined in the Prefect Python API, for example `LocalFSBlock` has a `write_path()` method attached which only writes to paths relative from the block basepath.

# Examples:

```jldoctest
julia> using PrefectInterfaces

julia> spec_fsblock = LocalFSBlock("local-file-system/xanadu", "local-file-system", "/usr/mahiki/xanadu/dev");

julia> fsblock = PrefectBlock("local-file-system/xanadu", spec_fsblock);

julia> fsblock.blockname
"local-file-system/xanadu"

julia> propertynames(fsblock.block)
(:blockname, :blocktype, :basepath, :read_path, :write_path)

julia> fsblock.block.basepath
"/usr/mahiki/xanadu/dev"
```
