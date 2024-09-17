# Orion Library
This documentation is for the stable release of Orion Library.

## Booting the Library
```lua
local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/rainhitgrassed/mine/main/Source')))()
```



## Creating a Window
```lua
local Window = OrionLib:MakeWindow({Name = "Lightning.cc", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})

```



## Creating a Tab
```lua
local Tab = Window:MakeTab({
	Name = "Catching",
	Icon = "rbxassetid://4483362458",
	PremiumOnly = false
})

```
## Creating a Section
```lua
local Section = Tab:AddSection({
	Name = "Section"
})

```
You can add elements to sections the same way you would add them to a tab normally.

## Notifying the user
```lua
OrionLib:MakeNotification({
	Name = "Title!",
	Content = "Notification content... what will it say??",
	Image = "rbxassetid://4483345998",
	Time = 5
})

```



## Creating a Button
```lua
Tab:AddButton({
	Name = "Button!",
	Callback = function()
      		print("button pressed")
  	end    
})

```


## Creating a Checkbox toggle
```lua
Tab:AddToggle({
	Name = "This is a toggle!",
	Default = false,
	Callback = function(Value)
		print(Value)
	end    
})

```

## Creating a Slider
```lua
Tab:AddSlider({
	Name = "Magnet Radius",
	Min = 0,
	Max = 25,
	Default = 0,
	Color = Color3.fromRGB(109,22,197),
	Increment = 1,
	ValueName = "Magnet Range",
	Callback = function(Value)
		print(Value)
	end    
})

```

## Creating a Label
```lua
Tab:AddLabel("Label")
```


## Creating a Paragraph
```lua
Tab:AddParagraph("Paragraph","Paragraph Content")
```

## Creating an Adaptive Input
```lua
Tab:AddTextbox({
	Name = "Textbox",
	Default = "default box input",
	TextDisappear = true,
	Callback = function(Value)
		print(Value)
	end	  
})

```


## Creating a Keybind
```lua
Tab:AddBind({
	Name = "Bind",
	Default = Enum.KeyCode.E,
	Hold = false,
	Callback = function()
		print("press")
	end    
})

```

## Creating a Dropdown menu
```lua
Tab:AddDropdown({
	Name = "Dropdown",
	Default = "1",
	Options = {"1", "2"},
	Callback = function(Value)
		print(Value)
	end    
})

```

### Adding a set of new Dropdown buttons to an existing menu
```lua
Dropdown:Refresh(List<table>,true)
```

The above boolean value "true" is whether or not the current buttons will be deleted.
### Selecting a dropdown option
```lua
Dropdown:Set("dropdown option")
```

# Finishing your script (REQUIRED)
The below function needs to be added at the end of your code.
```lua
OrionLib:Init()
```

### How flags work.
The flags feature in the ui may be confusing for some people. It serves the purpose of being the ID of an element in the config file, and makes accessing the value of an element anywhere in the code possible.
Below in an example of using flags.
```lua
Tab1:AddToggle({
    Name = "Toggle",
    Default = true,
    Save = true,
    Flag = "toggle"
})

print(OrionLib.Flags["toggle"].Value) -- prints the value of the toggle.
```
Flags only work with the toggle, slider, dropdown, bind, and colorpicker.

### Making your interface work with configs.
In order to make your interface use the configs function you first need to add the `SaveConfig` and `ConfigFolder` arguments to your window function. The explanation of these arguments in above.
Then you need to add the `Flag` and `Save` values to every toggle, slider, dropdown, bind, and colorpicker you want to include in the config file.
The `Flag = <string>` argument is the ID of an element in the config file.
The `Save = <bool>` argument includes the element in the config file.
Config files are made for every game the library is launched in.

## Destroying the Interface
```lua
OrionLib:Destroy()
```
