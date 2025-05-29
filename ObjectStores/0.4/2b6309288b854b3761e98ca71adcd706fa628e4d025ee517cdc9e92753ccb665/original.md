Required fields:

  * id::String;                                     # From Authorization.AbstractClient
  * id2permission::Dict{String, Permission};        # Resource ID => Permission (from Authorization.AbstractClient)
  * idpattern2permission::Dict{Regex, Permission};  # Resource ID pattern => Permission (from Authorization.AbstractClient)
  * type2permission::Dict{DataType, Permission};    # Resource type => Permission (from Authorization.AbstractClient)
  * rootbucketID::String  # ID of root bucket       # Specific to ObjectStores
