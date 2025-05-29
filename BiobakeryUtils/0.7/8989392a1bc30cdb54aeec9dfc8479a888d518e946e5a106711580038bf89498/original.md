```
function humann_regroup(comm::CommunityProfile; inkind="uniref90", outkind::String="ec")
```

Wrapper for `humann_regroup_table` script to convert table from one kind of functional mapping to another.

Requires installation of [`humann`](https://github.com/biobakery/humann) available in `ENV["PATH"]`. See "[Using Conda](@ref using-conda)" for more information.
