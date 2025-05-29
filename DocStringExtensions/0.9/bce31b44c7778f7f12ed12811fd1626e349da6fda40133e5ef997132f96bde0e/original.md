Defines a docstring template that will be applied to all docstrings in a module that match the specified category or tuple of categories of documented bindings.

Effectively, it replaces all the matching docstrings in the module with the template. The `DOCSTRING` abbreviation can be used to splice the original docstring into the replacement docstring generated from the template.

# Examples

```julia
@template DEFAULT =
    """
    $(SIGNATURES)
    $(DOCSTRING)
    """
```

`DEFAULT` is the default template that is applied to a docstring if no other template definitions match the documented expression. The `DOCSTRING` abbreviation is used to mark the location in the template where the actual docstring body will be spliced into each docstring.

```julia
@template (FUNCTIONS, METHODS, MACROS) =
    """
    $(SIGNATURES)
    $(DOCSTRING)
    $(METHODLIST)
    """
```

A tuple of categories can be specified when a docstring template should be used for several different categories.

```julia
@template MODULES = ModName
```

The template definition above will define a template for module docstrings based on the template for modules found in module `ModName`.

!!! note
    Supported categories are `DEFAULT`, `FUNCTIONS`, `METHODS`, `MACROS`, `TYPES`, `MODULES`, and `CONSTANTS`.

