```
function import_project_info(; format=nothing, data, url=get_url(), token=get_token(),)
```

Import basic attributes of a REDCap project

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `data`: May be a String, a file name, or a data type such as NamedTuple or Dict. Availabel attributes are project*title, project*language, purpose, purpose*other, project*notes, custom*record*label, secondary*unique*field, is*longitudinal, surveys*enabled, scheduling*enabled, record*autonumbering*enabled, randomization*enabled, project*irb*number, project*grant*number, project*pi*firstname, project*pi*lastname, display*today*now*button, iand bypass*branching*erase*field_prompt.
  * `format`: the format of the `data` input parameter: `:csv`, `:json`, or `:xml` (default). If `data` is a String or a file name, this value must indicate the correct format. If `data` is a NamedTuple, Dict, or similar type, this value will determine what format will be used internally to pass on the data.
