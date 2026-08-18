local Library = loadstring(readfile('https://raw.githubusercontent.com/veracrypter/skeetoria/refs/heads/main/LibraryManager.lua'))()
local ThemeManager = loadstring(readfile('https://raw.githubusercontent.com/veracrypter/skeetoria/refs/heads/main/ThemeManager.lua'))()
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/veracrypter/skeetoria/refs/heads/main/SaveManager.lua"))()


local Window = Library:CreateWindow({
    Title = 'skeetoria',
    Center = true,
    AutoShow = true,
    Size = UDim2.fromOffset(620, 600),
    SidebarWidth = 58,
    SidebarOrder = { 'Rage', 'AntiAim', 'Aimbot', 'Visuals', 'Settings', 'Weapons', 'PlayerList', 'Configs', 'Lua' },
    MenuFadeTime = 0.15
})

local Rage = Window:AddTab({ Name = 'Rage', Icon = 'Rage' })
local Aimbot = Window:AddTab({ Name = 'Aimbot', Icon = 'Aimbot' })
local AntiAim = Window:AddTab({ Name = 'AntiAim', Icon = 'AntiAim' })
local Visuals = Window:AddTab({ Name = 'Visuals', Icon = 'Visuals' })
local Weapons = Window:AddTab({ Name = 'Weapons', Icon = 'Weapons' })
local Settings = Window:AddTab({ Name = 'Settings', Icon = 'Settings' })
local Players = Window:AddTab({ Name = 'PlayerList', Icon = 'PlayerList' })
local Configs = Window:AddTab({ Name = 'Configs', Icon = 'Configs' })
local Lua = Window:AddTab({ Name = 'Lua', Icon = 'Lua' })

local Ragebot = Rage:AddLeftGroupbox('Ragebot')
Ragebot:AddToggle('RageEnabled', { Text = 'Enabled' }):AddKeyPicker('RageKey', {
    Default = 'None',
    Text = 'Ragebot',
    Mode = 'Toggle',
    SyncToggleState = true
})
Ragebot:AddSlider('RageFov', { Text = 'FOV', Default = 90, Min = 0, Max = 360, Rounding = 0, Suffix = '°' })
Ragebot:AddDropdown('TargetSelection', { Text = 'Target selection', Values = { 'Cursor', 'Distance', 'Lowest HP' }, Default = 1 })

local Aim = Aimbot:AddLeftGroupbox('Aimbot')
Aim:AddToggle('AimbotEnabled', { Text = 'Enabled' })
Aim:AddSlider('AimSmoothness', { Text = 'Smoothness', Default = 35, Min = 0, Max = 100, Rounding = 0, Suffix = '%' })

local AA = AntiAim:AddLeftGroupbox('Anti-aim')
AA:AddToggle('AAEnabled', { Text = 'Enabled' })
AA:AddDropdown('AAMode', { Text = 'Mode', Values = { 'Static', 'Jitter', 'Random' }, Default = 1 })

local ESP = Visuals:AddLeftGroupbox('Players')
ESP:AddToggle('ESPEnabled', { Text = 'ESP', Default = true }):AddColorPicker('ESPColor', {
    Default = Color3.new(1, 1, 1),
    Title = 'ESP color'
})
ESP:AddDropdown('ESPFlags', {
    Text = 'Flags',
    Values = { 'Distance', 'Weapon', 'Armor', 'Downed' },
    Multi = true,
    Default = { 'Distance', 'Weapon' }
})

Weapons:AddLeftGroupbox('Weapon visuals'):AddToggle('WeaponChams', { Text = 'Weapon chams' })
Players:AddLeftGroupbox('Players'):AddDropdown('SelectedPlayer', { Text = 'Player', SpecialType = 'Player', AllowNull = true })
Lua:AddLeftGroupbox('Lua'):AddButton('Test notification', function()
    Library:Notify('skeetoria loaded', 3)
end)

local Menu = Settings:AddLeftGroupbox('Menu')
Menu:AddLabel('Menu key'):AddKeyPicker('MenuKeybind', {
    Default = 'Insert',
    NoUI = true,
    Text = 'Menu key',
    Mode = 'Toggle'
})
Library.ToggleKeybind = Options.MenuKeybind

Menu:AddToggle('ShowKeybinds', { Text = 'Keybind list' }):OnChanged(function(state)
    Library.KeybindFrame.Visible = state
end)

Menu:AddToggle('ShowWatermark', { Text = 'Watermark' }):OnChanged(function(state)
    Library:SetWatermarkVisibility(state)
end)

Library:SetWatermark('skeetoria')
Library:SetWatermarkVisibility(false)

ThemeManager:SetLibrary(Library)
ThemeManager:SetFolder('skeetoria')
SaveManager:SetLibrary(Library)
SaveManager:SetFolder('skeetoria')
SaveManager:IgnoreThemeSettings()
ThemeManager:ApplyToTab(Settings)
SaveManager:BuildConfigSection(Configs)
SaveManager:LoadAutoloadConfig()
