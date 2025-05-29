```julia
copy(
    exo::Exodus.ExodusDatabase,
    new_file_name::String;
    mesh_only_flag
)

```

Used to copy an ExodusDatabase. As of right now this is the best way to create a new ExodusDatabase for output. Not all of the put methods have been wrapped and properly tested. This one has though.
