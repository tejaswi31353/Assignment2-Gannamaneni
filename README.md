# Assignment2-Gannamaneni
# Tejaswi Gannamaneni 
##### Cleveland

Reason : Cleveland, officially the City of Cleveland, is a major city in the U.S. state of **Ohio**, and the county seat of **Cuyahoga County**. It is located along the southern shore of **Lake Erie**, across the U.S. maritime border with Canada and approximately 60 miles west of the **Ohio-Pennsylvania** state border. Thats the main reason i like that place.

---
## Travel Instructions

1. The total driving time is 12 hours, 50 minutes estimatedly, from Maryville to Cleveland.
2. Each time, I visit,Cleveland opens a new chapter from past.
3. There are many options to reach Cleveland i.e. by Drive, by flight, by public transport or private transport.etc..
4. If you are from other country you need to have a valid visa to enter into the 'USA'
5. Quick and useful information about Cleveland travel:
    1. language spoken: Only English
    2. beautiful parklands, vibrant art and culture scene, musical history. It has several sports teams (Browns, Cavaliers) and is often called the birthplace of rock and roll.
    3. It is a major city in the state of 'Ohio'
6. where to stay in Cleveland:
    1. Prefer to rent an apartment when you travel with top-rated and most beautiful Airbnbs and vacation rentals in neighborhoods all around the city of Cleveland.
    2. Staying in the Downtown Cleveland hotel.
    3. Staying at Hilton Cleveland Downtown.

    ### Must-carry things on a trip to Cleveland.

    * Dress.
        * warm Pants or Jeans.
    * Umbrella And Rain coat
        * Just in case if it rains or you need shelter in sun light or when raining.
    * Mirrored sunglasses
        * Protects eyes and skin from UV rays comes directly from sun.


Link to AboutMe: 
[AboutMe](https://github.com/tejaswi31353/Assignment2-Gannamaneni/blob/main/AboutMe.md)

---

## Table for Food Meanu

| Food | Location | Cost |
| ---| ---| ---: |
| Vada Pav | Mumbai | 10Rs/- |
| Chicken Noodles | Hyderabad | 200Rs/- |
| Muttoon Biryani | Hyderabad | 500Rs/- |
| Sambar Vada | Chennai | 100Rs/- |

---
## Pithy Quotes

> “Many of life’s failures are people who did not realize how close they were to success when they gave up.” <br> By:– *Thomas A. Edison*


>  “Never let the fear of striking out keep you from playing the game.”<br> By:– *Babe Ruth*

---

## Code Fencing

Description: 
> The algorithm first finds the leftmost and rightmost points A and B. In the event multiple such points exist, the lowest among the left (lowest Y-coordinate) is taken as A, and the highest among the right (highest Y-coordinate) is taken as B. Clearly, A and B must both belong to the convex hull as they are the farthest away and they cannot be contained by any line formed by a pair among the given points.<br>

> Now, draw a line through AB. This divides all the other points into two sets, S1 and S2, where S1 contains all the points above the line connecting A and B, and S2 contains all the points below the line joining A and B. The points that lie on the line joining A and B may belong to either set. The points A and B belong to both sets. Now the algorithm constructs the upper set S1 and the lower set S2 and then combines them to obtain the answer.

Here is the link:<https://cp-algorithms.com/geometry/grahams-scan-convex-hull.html>

Here is the code for `Convex Hull construction using Graham's Scan`:
```
struct pt {
    double x, y;
};

bool cmp(pt a, pt b) {
    return a.x < b.x || (a.x == b.x && a.y < b.y);
}

bool cw(pt a, pt b, pt c) {
    return a.x*(b.y-c.y)+b.x*(c.y-a.y)+c.x*(a.y-b.y) < 0;
}

bool ccw(pt a, pt b, pt c) {
    return a.x*(b.y-c.y)+b.x*(c.y-a.y)+c.x*(a.y-b.y) > 0;
}

void convex_hull(vector<pt>& a) {
    if (a.size() == 1)
        return;

    sort(a.begin(), a.end(), &cmp);
    pt p1 = a[0], p2 = a.back();
    vector<pt> up, down;
    up.push_back(p1);
    down.push_back(p1);
    for (int i = 1; i < (int)a.size(); i++) {
        if (i == a.size() - 1 || cw(p1, a[i], p2)) {
            while (up.size() >= 2 && !cw(up[up.size()-2], up[up.size()-1], a[i]))
                up.pop_back();
            up.push_back(a[i]);
        }
        if (i == a.size() - 1 || ccw(p1, a[i], p2)) {
            while(down.size() >= 2 && !ccw(down[down.size()-2], down[down.size()-1], a[i]))
                down.pop_back();
            down.push_back(a[i]);
        }
    }

    a.clear();
    for (int i = 0; i < (int)up.size(); i++)
        a.push_back(up[i]);
    for (int i = down.size() - 2; i > 0; i--)
        a.push_back(down[i]);
}

```
Here is the link: <https://cp-algorithms.com/geometry/grahams-scan-convex-hull.html>
