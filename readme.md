# CodeClub Project 

![present pic](images/present1.png)

## Christmas Present Exchange

In this project, we will make a wrapped present and then reveal the gift underneath. We will then create and send presents to each other!

This project uses the PyProcessing library rather than Turtle for making screen pictures. You can see a reference to the ways we can draw here: [https://py.processing.org/reference/](https://py.processing.org/reference/). Processing has a function to set up the screen, then one to update it within a loop, allowing animation etc.

1. Go to the starting project : [https://trinket.io/python/d2c7f82708](https://trinket.io/python/d2c7f82708). See we have a python "dictionary" for holding the data about the present. 

2. Let's start with the wrapping paper. We want to add code to the setup function at line 14. 

```python
    # Wrapping paper
    fill(204, 12, 0)
    rect(0,0,500,500)
    noFill()
    stroke(50, 0, 100)
    strokeWeight(20)
    line(0,240,500,240)
    line(240,0,240,500)
    line(240,240,320,300)
    line(240,240,160,300)
    ellipse(240, 160, 55, 135)
```

3. Test the program by running it. Notice that the run() function means that the program keeps running until we click Stop.

4. The "fill" function is the RGB (Red, green and blue) values we have worked with before, which go from 0 to 255. Try changing the values and changing your wrapping paper.

5. Let's add some Text to the gift. We can add the draw() function in between setup() and run() to do this. See that the function is using the text from our Dictionary at the top.

```python
def draw():
  # Create message
  textSize(60)
  fill(40, 255, 0)
  text(myPresent["message"], 20, 60)
  text("From "+ myPresent["from"], 120, 470)
```

6. Hit Run to test. Again, note that you can change the size, colour and position of the text by changing the numbers.

7. Now for the present! We need to load an image in the setup() function using the URL (web link) in the Dictionary.

```python
    # Load the image from the web site - this goes at the end of the setup function
    url = myPresent["present"]
    global webImg
    webImg = loadImage(url, "jpg")
```

8. We won't see anything yet, but we will reveal the present on a mouse click, with a new function just before the run() line:

```python
def mousePressed(): 
    image(webImg, 0, 0, 500,500)
```

9. Now we can prepare and send a present to someone! Change the __present__, the __message__ and the __from__ and __to__ in our dictionary at line 5. 

```python
myPresent = {
  "to":"Paul",
  "from":"Alex",
  "message": "Message to them!",
  "present": "https://change.this.link"
}
```

10. For this, we need to avoid running the run() function at the end, so let's comment that out and then ask our Santa python to send it.

```python
  #run()
  santa.sendPresent(myPresent)
```
11. Has anyone given us a present? Let's check. Comment out the send present and check for presents with your name on!
```python
  # run()
  # santa.sendPresent(myPresent)
  santa.checkPresents("Paul")
```
12. If you have a new present, put it at the top of your code as the value for myPresent and then see what you have got! __Remember to uncomment the run function__.