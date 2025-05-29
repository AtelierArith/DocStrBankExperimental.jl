```
 visualize(curriculum; <keyword arguments>))
```

Visualize a curriculum. 

# Arguments

Required:

  * `curriculum::Curriculum` : the curriculum to visualize.

Keyword:

  * `changed` : callback function argument, called whenever the curriculum is modified through the interface.    Default is `nothing`.
  * `notebook` : a Boolean argument, if set to `true`, Blink will not create a new window for the visualization, which allows it to be displayed in the output cell of a Jupyter notebook.
  * `serve_local`: a Boolean argument, if set to `true`, the visualization will be served through localhost; otherwise, a preset remote server (Internet required).  Default is `false`.
  * `edit` : a Boolean argument, if set to `true`, the user may edit the curriculum through the visualziation interface.   Default is `false`.
  * `output_file` : the relative or absolute path to the CSV file that will store the edited curriculum. Default   is `edited_curriculum.csv`.
  * `show_delay` : a Boolean argument, if set to `true`, the delay factor metric will be displayed in the tooltip when hovering over a course. Default is `false`.
  * `show_blocking` : a Boolean argument, if set to `true`, the blocking factor metric will be displayed in the tooltip when hovering over a course. Default is `false`.
  * `show_centrality` : a Boolean argument, if set to `true`, the centrality metric will be displayed in the tooltip when hovering over a course. Default is `false`.
  * `show_complexity` : a Boolean argument, if set to `true`, the complexity metric will be displayed in the tooltip when hovering over a course. Default is `false`.
  * `scale` : a Real value used to scale the size of the output window.
