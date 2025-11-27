local Player = game.Players.LocalPlayer
local Mouse = Player:GetMouse()local ScreenGui = Instance.new("ScreenGui")local Frame = Instance.new("Frame")local PassBox = Instance.new("TextBox")local Enter = Instance.new("TextButton")local SavePos = Instance.new("TextButton")local LoadPos = Instance.new("TextButton")ScreenGui.Parent = game.CoreGui
ScreenGui.Name ="TeleportGUI"Frame.Parent = ScreenGui
Frame.Size = UDim2.new(0, 300, 0, 200)Frame.Position = UDim2.new(0.5, -150, 0.5, -100)Frame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)Frame.BorderSizePixel = 0
Frame.Active = true
Frame.Draggable = true

local Corner = Instance.new("UICorner", Frame)Corner.CornerRadius = UDim.new(0, 12)PassBox.Parent = Frame
PassBox.Size = UDim2.new(0, 260, 0, 50)PassBox.Position = UDim2.new(0.5, -130, 0, 20)PassBox.BackgroundColor3 = Color3.fromRGB(40, 40, 40)PassBox.TextColor3 = Color3.fromRGB(0, 255, 0)PassBox.PlaceholderText ="Enter Password..."PassBox.Text = ""PassBox.Font = Enum.Font.Code
PassBox.TextSize = 24
PassBox.ClearTextOnFocus = false

local PassCorner = Instance.new("UICorner", PassBox)PassCorner.CornerRadius = UDim.new(0, 8)Enter.Parent = Frame
Enter.Size = UDim2.new(0, 260, 0, 40)Enter.Position = UDim2.new(0.5, -130, 0, 80)Enter.BackgroundColor3 = Color3.fromRGB(0, 170, 0)Enter.Text ="Enter (0000)"Enter.TextColor3 = Color3.new(1,1,1)Enter.Font = Enum.Font.GothamBold
Enter.TextSize = 20

local EnterCorner = Instance.new("UICorner", Enter)local savedPos = nil

Enter.MouseButton1Click:Connect(function()    if PassBox.Text =="0000" then
        PassBox.Visible = false
        Enter.Visible = false
        
        SavePos.Parent = Frame
        SavePos.Size = UDim2.new(0, 120, 0, 50)        SavePos.Position = UDim2.new(0, 20, 0, 130)        SavePos.BackgroundColor3 = Color3.fromRGB(0, 200, 0)        SavePos.Text ="Save Pos"        SavePos.TextColor3 = Color3.new(0,0,0)        SavePos.Font = Enum.Font.GothamBold
        SavePos.TextSize = 18
        Instance.new("UICorner", SavePos).CornerRadius = UDim.new(0, 8)        
        LoadPos.Parent = Frame
        LoadPos.Size = UDim2.new(0, 120, 0, 50)        LoadPos.Position = UDim2.new(0, 160, 0, 130)        LoadPos.BackgroundColor3 = Color3.fromRGB(0, 150, 0)        LoadPos.Text ="Load Pos"        LoadPos.TextColor3 = Color3.new(0,0,0)        LoadPos.Font = Enum.Font.GothamBold
        LoadPos.TextSize = 18
        Instance.new("UICorner", LoadPos).CornerRadius = UDim.new(0, 8)    end
end)SavePos.MouseButton1Click:Connect(function()    if Player.Character and Player.Character:FindFirstChild("HumanoidRootPart") then
        savedPos = Player.Character.HumanoidRootPart.Position
        SavePos.Text ="Saved!"        wait(1)        SavePos.Text ="Save Pos"    end
end)LoadPos.MouseButton1Click:Connect(function()    if savedPos and Player.Character and Player.Character:FindFirstChild("HumanoidRootPart") then
        Player.Character.HumanoidRootPart.CFrame = CFrame.new(savedPos)    end
end)```
