# Who am I?
Hello, my name is Martin Vitus Petersen, also known, in most places, as vitu0089.

Born in 2002, I always like computers, maybe a little too much. Playing games became my mornings, schooldays, and afternoons. After a while, it just gets a bit boring, just playing them. Actually making them proved a larger challenge than I thought it would, but in 2018, I made a few games on Scratch. They were terrible, and I hate myself for it, but they were the reason I began programming. I quickly switched over to LuaU (Roblox) scripting, and after a while, I was making something that actually looked like solid code. Since I began coding, there has not been a day that I haven't thought about coding, not a week without coding, and not a month without a new project.

As I have been coding for a solid 5 years at this point, I thought making a portfolio was due, so I will be trying my best to document a few of my projects. I will of course start with the ones I am most proud of, working my way down.

# Portfolio
### Kingmaker:
![image](https://github.com/vitu0089/RobloxPortfolio/assets/86110418/e89de738-6d28-467c-b2e4-32bf873c8ba3)

As I had been working on games of low quality for a while as a freelancer, I wanted to make something a little more serious. Though I haven't finished it yet, I haven't given up on it either. Most code was written in a separate place, then imported when the game started up. This gave me some pretty unique problems like scripts not being present for certain events. This was also the one time I decided to make a large map myself, using Blender and Roblox together, as seen below.

![image](https://github.com/vitu0089/RobloxPortfolio/assets/86110418/4e127985-55a1-49ca-bee0-1073ac929b6e)

### Miners Bar:
![image](https://github.com/vitu0089/RobloxPortfolio/assets/86110418/22833048-af7a-424b-9b75-1c58f1d48d2d)

Making tycoons has always been one of my favorite programming tasks, if only I was as good at building as I was at coding. I tend to give up on tycoons, but this one nears its completion. The only reason behind its non-release is the fact that I might not be able to make enough content for the game. Also, I have a floor of the building just... not populated with anything. I hope to find someone willing to help me with the project, as I don't see myself releasing it before 2024.

### Bezier Curve
As a small project, I wanted to display a bezier curve in 3D. I found most of this code online, but I don't believe in copy-pasting. I want to understand what goes on when I write something, so I looked around on the internet for a mathematical explanation of how and why bezier curves work. And after a while, things started to make sense.

```lua
local T = 0
local Curve = game.ReplicatedStorage.QuadraticCurve:Clone(); Curve.Parent = workspace
local Increments = 0.1

local function MovePoint(TrailPart)
	local FirstLine,SecondLine = {},{}
	
	for i=1,3 do
		FirstLine[i] = Curve[tostring(i)].Position + (Curve[tostring(i + 1)].Position - Curve[tostring(i)].Position) * T
	end

	for i=1,2 do
		SecondLine[i] = FirstLine[i] + (FirstLine[i + 1] - FirstLine[i]) * T
	end
	
	TrailPart.Position = SecondLine[1] + (SecondLine[2] - SecondLine[1]) * T
end

local function CreateCurve(Distance)
	if workspace:FindFirstChild("TracePart") then
		workspace["TracePart"]:Destroy()
	end
	
	Distance = Distance or 1
	
	local TrailPart = game.ReplicatedStorage.TracePart:Clone(); TrailPart.Parent = workspace
	local Forwards = true
	
	if T == Distance then
		Forwards = false
	elseif T == 0 then
		Forwards = true
	else
		print("Didn't work")
		return
	end
	
	for i=1,(1 / Increments) do
		MovePoint(TrailPart)
		
		T += Forwards and Increments or -Increments
		T = math.clamp(math.round(T * (1 / Increments)),0,(Distance / Increments)) / (1 / Increments)
		
		task.wait()
	end
	
	MovePoint(TrailPart)
end

script.Parent.ConfirmButton.MouseButton1Click:Connect(function()
	CreateCurve()
end)
```
![image](https://github.com/vitu0089/RobloxPortfolio/assets/86110418/5b347051-1683-4483-907f-922b7ad71c43)
![image](https://github.com/vitu0089/RobloxPortfolio/assets/86110418/e8e51449-6f00-43d3-a40b-6cbed5b65503)

# End Note
I must admit, my coding methods have changed a lot in the past few years, mostly for the better, and if you wish to see a live demonstration of such, please head over to Discord and hit me up.

# Conclusion
If you wish me to work with you, please DM me on Discord (vitu0089), and propose your project, I'll gladly try to help you.



### Best Regards
MVP, vitu0089
