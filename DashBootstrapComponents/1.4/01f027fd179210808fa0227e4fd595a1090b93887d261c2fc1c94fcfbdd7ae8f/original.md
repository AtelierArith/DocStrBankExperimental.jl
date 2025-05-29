```
dbc_tab(;kwargs...)
dbc_tab(children::Any;kwargs...)
dbc_tab(children_maker::Function;kwargs...)
```

A Tab component. Create a single tab. Should be used as a component of Tabs. Keyword arguments:

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `activeLabelClassName` (String; optional): **DEPRECATED** Use `active_label_class_name` instead

Often used with CSS to style elements with common properties. The classes specified with this prop will be applied to the NavLink in the tab when it is active.

  * `activeTabClassName` (String; optional): **DEPRECATED** Use `active_tab_class_name` instead

Often used with CSS to style elements with common properties. The classes specified with this prop will be applied to the NavItem in the tab when it is active.

  * `active_label_class_name` (String; optional): Often used with CSS to style elements with common properties. The classes

specified with this prop will be applied to the NavLink in the tab when it is active.

  * `active_label_style` (Dict; optional): Defines CSS styles which will override styles previously set. The styles

set here apply to the NavLink in the tab when it is active

  * `active_tab_class_name` (String; optional): Often used with CSS to style elements with common properties. The classes

specified with this prop will be applied to the NavItem in the tab when it is active.

  * `active_tab_style` (Dict; optional): Defines CSS styles which will override styles previously set. The styles

set here apply to the NavItem in the tab when it is active.

  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

Often used with CSS to style elements with common properties.

  * `class_name` (String; optional): Often used with CSS to style elements with common properties.
  * `disabled` (Bool; optional): Determines if tab is disabled or not - defaults to false
  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `label` (String; optional): The tab's label, displayed in the tab itself.
  * `labelClassName` (String; optional): **DEPRECATED** Use `label_class_name` instead

Often used with CSS to style elements with common properties. The classes specified with this prop will be applied to the NavLink in the tab.

  * `label_class_name` (String; optional): Often used with CSS to style elements with common properties. The classes

specified with this prop will be applied to the NavLink in the tab.

  * `label_style` (Dict; optional): Defines CSS styles which will override styles previously set. The styles

set here apply to the NavLink in the tab.

  * `loading_state` (optional): Object that holds the loading state object coming from dash-renderer. loading*state has the following type: lists containing elements 'is*loading', 'prop*name', 'component*name'.

Those elements have the following types:

  * `is_loading` (Bool; optional): Determines if the component is loading or not
  * `prop_name` (String; optional): Holds which property is loading
  * `component_name` (String; optional): Holds the name of the component that is loading
  * `style` (Dict; optional): Defines CSS styles which will override styles previously set. The styles

set here apply to the content of the Tab

  * `tabClassName` (String; optional): **DEPRECATED** Use `tab_class_name` instead

Often used with CSS to style elements with common properties. The classes specified with this prop will be applied to the NavItem in the tab.

  * `tab_class_name` (String; optional): Often used with CSS to style elements with common properties. The classes

specified with this prop will be applied to the NavItem in the tab.

  * `tab_id` (String; optional): Optional identifier for tab used for determining which tab is visible

if not specified, and Tab is being used inside Tabs component, the tabId will be set to "tab-i" where i is (zero indexed) position of tab in list tabs pased to Tabs component.

  * `tab_style` (Dict; optional): Defines CSS styles which will override styles previously set. The styles

set here apply to the NavItem in the tab.
