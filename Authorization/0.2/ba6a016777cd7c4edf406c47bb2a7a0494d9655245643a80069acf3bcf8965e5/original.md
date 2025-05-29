Required fields:

  * id::String;
  * id2permission::Dict{String, Permission};        # Resource ID => Permission
  * idpattern2permission::Dict{Regex, Permission};  # Resource ID pattern => Permission
  * type2permission::Dict{DataType, Permission};    # Resource type => Permission
