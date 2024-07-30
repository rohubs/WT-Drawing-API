---

# WA_Drawing Library 🎨

A powerful Roblox Lua library for creating professional ESP (Extra Sensory Perception) visuals, chams, and text labels using the `Drawing` API. Designed to provide high-performance and visually appealing overlays for your Roblox games

## Installation 🚀

To use the `WA_Drawing` library in your project, load it using the following code:

```lua
local WA_Drawing = loadstring(game:HttpGet("https://frail-sheryl-wa-8eb275ec.koyeb.app/raw/script/wt_api", true))()
```

## Functions 📚

### 1. `WA_Drawing.ESP_BOX` 📦

Creates a 2D ESP box around a part with optional rainbow outline.

#### Syntax

```lua
local espBox = WA_Drawing.ESP_BOX(part, colorOutline, rainbow)
```

#### Arguments

- `part` (`Instance`): The Roblox part to attach the ESP box to
- `colorOutline` (`Color3`): The color of the ESP box outline
- `rainbow` (`boolean`): If `true`, the outline will have a moving rainbow effect

#### Methods

- `espBox:Draw()`: Updates the ESP box position and size
- `espBox:Remove()`: Removes the ESP box from the screen


#### Example

```lua
local espBox = WA_Drawing.ESP_BOX(part, Color3.fromRGB(255, 0, 0), true)

game:GetService("RunService").RenderStepped:Connect(function()
    espBox:Draw()
end)
```

### 2. `WA_Drawing.Chams` ✨

Creates a chams (colored highlight) effect on a part

#### Syntax

```lua
local cham = WA_Drawing.Chams(part, color, transparency)
```

#### Arguments

- `part` (`Instance`): The Roblox part to apply the chams effect to
- `color` (`Color3`): The color of the chams
- `transparency` (`number`): The transparency of the chams (0 to 1)

#### Methods

- `cham:Remove()`: Removes the chams effect from the part

#### Example

```lua
local cham = WA_Drawing.Chams(part, Color3.fromRGB(0, 255, 0), 0.3)

-- To remove the cham later
-- cham:Remove()
```

### 3. `WA_Drawing.TextLabel` 🏷️

Creates a text label that follows a part, acting like an ESP

#### Syntax

```lua
local textLabel = WA_Drawing.TextLabel(text, part, size, color)
```

#### Arguments

- `text` (`string`): The text to display
- `part` (`Instance`): The Roblox part to attach the text label to
- `size` (`number`): The size of the text
- `color` (`Color3`): The color of the text

#### Methods

- `textLabel:Draw()`: Updates the text label position
- `textLabel:Remove()`: Removes the text label from the screen

#### Example

```lua
local textLabel = WA_Drawing.TextLabel("Hello, World!", part, 20, Color3.fromRGB(255, 255, 255))

game:GetService("RunService").RenderStepped:Connect(function()
    textLabel:Draw()
end)
```

### 4. Removing ESPs 🗑️

Functions to remove different types of ESP objects

#### Remove ESP Box

```lua
espBox:Remove()
```

#### Remove Chams

```lua
cham:Remove()
```

#### Remove TextLabel

```lua
textLabel:Remove()
```

## Full Example 📜

Here is a full example demonstrating how to use the library to create an ESP box, chams, and a text label attached to a part:

```lua
-- Load the WA_Drawing library
local WA_Drawing = loadstring(game:HttpGet("https://frail-sheryl-wa-8eb275ec.koyeb.app/raw/script/wt_api", true))()

-- Create a test part
local part = Instance.new("Part")
part.Size = Vector3.new(10, 10, 10)
part.Position = Vector3.new(0, 5, 0)
part.Anchored = true
part.Parent = workspace

-- Define colors for the ESP box
local colorOutline = Color3.fromRGB(255, 0, 0)  -- Red outline

-- Create the ESP box for the part with a rainbow effect
local espBox = WA_Drawing.ESP_BOX(part, colorOutline, true)

-- Draw the ESP box initially
espBox:Draw()

-- Update the ESP box continuously
game:GetService("RunService").RenderStepped:Connect(function()
    espBox:Draw()
end)

-- Create chams for the part
local cham = WA_Drawing.Chams(part, Color3.fromRGB(0, 255, 0), 0.3) -- Green cham with 30% transparency

-- To remove the cham later, call cham:Remove()

-- Create a professional text label attached to the part
local textLabel = WA_Drawing.TextLabel("Hello, World!", part, 20, Color3.fromRGB(255, 255, 255)) -- White text

-- Update the text label position
game:GetService("RunService").RenderStepped:Connect(function()
    textLabel:Draw()
end)

-- To remove the text label later, call textLabel:Remove()

-- Example to remove the ESP box
-- espBox:Remove()

-- Example to remove the text label
-- textLabel:Remove()

-- Example to remove the chams
-- cham:Remove()

```


