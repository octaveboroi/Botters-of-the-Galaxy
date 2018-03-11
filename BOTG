import sys
import math
from random import shuffle


PLACES=[]
ITEMS=[]
cpt=-4
items_owner=[]
QG_friend, QG_unfriend=False, False
HEROS=['DEADPOOL','HULK','VALKYRIE','IRONMAN','DOCTOR_STRANGE']
shuffle(HEROS) #for choice 2 random heros
DEADPOOL=['COUNTER', 'WIRE', 'STEALTH',]
HULK=['CHARGE', 'EXPLOSIVESHIELD', 'BASH']
VALKYRIE=['SPEARFLIP', 'JUMP', 'POWERUP']
IRONMAN=['BLINK', 'FIREBALL', 'BURNING']
DOCTOR_STRANGE=['AOEHEAL', 'SHIELD', 'PULL']

def distance(a, b): return int(math.sqrt((abs(a.x-b.x)**2+abs(a.y-b.y)**2)))

def debug(*txt): print(*txt, file=sys.stderr)

class Player():
    def __init__(self):
        self.gold=0
        self.team=None
        
class Entity():
    def __init__(self, id, team, type, x, y, attackRange, health, maxHealth, shield, attackDamage, speed, stunDuration, gold, count1,
        count2, count3, mana, maxMana, regene, heroType, visible, items):
        self.id=int(id)
        self.team=int(team)
        self.type=type
        self.x=int(x)
        self.y=int(y)
        self.attackRange=int(attackRange)
        self.health=int(health)
        self.maxHealth=int(maxHealth)
        self.shield=int(shield)
        self.attackDamage=int(attackDamage)
        self.speed=int(speed)
        self.stunDuration=int(stunDuration)
        self.gold=int(gold)
        self.count1=int(count1)
        self.count2=int(count2)
        self.count3=int(count3)
        self.mana=int(mana)
        self.maxMana=int(maxMana)
        self.regene=int(regene)
        self.heroType=heroType
        self.visible=int(visible)
        self.items=int(items)
        self.possessed_items=[]        
        
    def show(self):
        return tuple((self.id, self.team, self.type, self.x, self.y, self.attackRange, self.health, self.maxHealth,
                     self.shield, self.attackDamage, self.speed, self.stunDuration, self.gold, self.count1, self.count2,
                     self.count3, self.mana, self.maxMana, self.regene, self.heroType, self.visible, self.items, len(self.objets), self.Objets()))
        
    def accessible_items(self):
	    return tuple(i for i in ITEMS if i.cost<=player.gold)
		
		
class Item():
    def __init__(self, name, cost, damage, health, maxHealth, mana, maxMana, speed, regene, potion):
        self.name=name
        self.cost=int(cost)
        self.damage=int(damage)
        self.health=int(health)
        self.maxHealth=int(maxHealth)
        self.mana=int(mana)
        self.maxMana=int(maxMana)
        self.speed=int(speed)
        self.regene=int(regene)
        self.potion=int(potion)

    def show(self): return self.name, self.cost, self.damage, self.health, self.maxHealth, self.mana, self.maxMana, self.speed, self.regene, self.potion


class Place():
    def __init__(self, type, x, y, radius):
        self.type=type
        self.x=int(x)
        self.y=int(y)
        self.radius=int(radius )

    def show(self): return self.type, self.x, self.y, self.radius

	
US, THEM= Player(), Player()
US.team=int(input())
THEM.team=abs(US.team-1)
for i in range(int(input())):
    PLACES.append(Place(*input().split()))

for i in range(int(input())):
    # item_name: contains keywords such as BRONZE, SILVER and BLADE, BOOTS connected by "_" to help you sort easier
    # item_cost: BRONZE items have lowest cost, the most expensive items are LEGENDARY
    # damage: keyword BLADE is present if the most important item stat is damage
    # move_speed: keyword BOOTS is present if the most important item stat is moveSpeed
    # is_potion: 0 if it's not instantly consumed
    ITEMS.append(Item(*input().split()))

# game loop
while True:
    cpt+=1 #cpt%15==0 new units
    entities=[]
    US.gold=(int(input()))
    THEM.gold=(int(input()))
    round_type = int(input())  # a positive value will show the number of heroes that await a command
    for i in range(int(input())):
        entities.append(Entity(*input().split()))
    if not QG_friend:
        QG_unfriend=[i for i in entities if i.team==THEM.team and i.type=='TOWER'].pop()
        QG_friend=[i for i in entities if i.team==US.team and i.type=='TOWER'].pop()
    # If roundType has a negative value then you need to output a Hero name, such as "DEADPOOL" or "VALKYRIE".
    # Else you need to output roundType number of any valid action, such as "WAIT" or "ATTACK unitId"
    if round_type<0: print(HEROS.pop())
    else:
        print('ATTACK_NEAREST HERO')
        if len([i for i in entities if i.team==US.team and i.type=='HERO'])==2:
            print('ATTACK_NEAREST HERO')
        
