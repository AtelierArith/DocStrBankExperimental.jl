delete_component!(c::T, w::Workflow)  where {T<:Component}

  * deletes a component if it was created for the current version or
  * mark its latest component revision as invalid
